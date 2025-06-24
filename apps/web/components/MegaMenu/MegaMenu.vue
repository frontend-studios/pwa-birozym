<template>
  <header ref="referenceRef" :class="headerClass" class="relative w-full md:sticky md:shadow-md z-10">
    <div
      class="navbar-top flex justify-between bg-white items-center flex-wrap md:flex-nowrap px-4 md:px-10 py-2 md:py-5 w-full border-0 border-neutral-200"
      data-testid="navbar-top"
    >
      <div class="flex items-center">
        <UiButton
          v-if="viewport.isLessThan('lg')"
          variant="tertiary"
          square
          :aria-label="t('closeMenu')"
          class="mr-5 active:bg-primary-500 hover:bg-primary-500"
          @click="openMenu([])"
        >
          <SfIconMenu class="text-primary-500 hover:text-white active:text-white" />
        </UiButton>

        <NuxtLink
          :to="localePath(paths.home)"
          :aria-label="t('goToHomepage')"
          class="flex shrink-0 w-full lg:w-48 items-center mr-auto text-white md:mr-10 focus-visible:outline focus-visible:outline-offset focus-visible:rounded-sm"
        >
          <UiVsfLogo />
        </NuxtLink>
      </div>

      <slot />
    </div>
  </header>
</template>

<script lang="ts" setup>
import {
  SfIconClose,
  SfDrawer,
  SfListItem,
  SfIconChevronRight,
  SfCounter,
  SfIconArrowBack,
  SfIconMenu,
  useTrapFocus,
  useDropdown,
} from '@storefront-ui/vue';
import { unrefElement } from '@vueuse/core';
import { type CategoryTreeItem, categoryTreeGetters } from '@plentymarkets/shop-api';
import { paths } from '~/utils/paths';
import type { MegaMenuProps } from '~/components/MegaMenu/types';

const props = defineProps<MegaMenuProps>();
const NuxtLink = resolveComponent('NuxtLink');

const { t } = useI18n();
const viewport = useViewport();
const localePath = useLocalePath();
const { buildCategoryMenuLink } = useLocalization();
const { headerBackgroundColor } = useSiteConfiguration();
const router = useRouter();
const { close, open, isOpen, activeNode, category, setCategory } = useMegaMenu();
const { setDrawerOpen } = useDrawerState();
const { referenceRef, floatingRef, style } = useDropdown({
  isOpen,
  onClose: close,
  placement: 'bottom-start',
  middleware: [],
});

const isTouchDevice = ref(false);
const categoryTree = ref(categoryTreeGetters.getTree(props.categories));
const drawerReference = ref();
const megaMenuReference = ref();
const triggerReference = ref();
const tappedCategories = ref<Map<number, boolean>>(new Map());
let removeHook: () => void;

const trapFocusOptions = {
  activeState: isOpen,
  arrowKeysUpDown: true,
  initialFocus: 'container',
} as const;

const activeMenu = computed(() => (category.value ? findNode(activeNode.value, category.value) : null));
const headerClass = computed(() => ({ 'z-[10]': isOpen.value }));

const findNode = (keys: number[], node: CategoryTreeItem): CategoryTreeItem => {
  if (keys.length > 1) {
    const [currentKey, ...restKeys] = keys;
    return findNode(restKeys, node.children?.find((child) => child.id === currentKey) || node);
  } else {
    return node.children?.find((child) => child.id === keys[0]) || node;
  }
};

const generateCategoryLink = (category: CategoryTreeItem) => {
  return buildCategoryMenuLink(category, categoryTree.value);
};

const openMenu = (menuType: number[]) => {
  activeNode.value = menuType;
  open();
  setDrawerOpen(true);
};

const goBack = () => {
  activeNode.value = activeNode.value.slice(0, -1);
};

const goNext = (key: number) => {
  activeNode.value = [...activeNode.value, key];
};

const focusTrigger = (index: number) => {
  unrefElement(triggerReference.value[index]).focus();
};

const onMouseLeave = () => {
  close();
  tappedCategories.value.clear();
};

const onCategoryMouseEnter = (menuNode: CategoryTreeItem) => {
  if (!viewport.isGreaterOrEquals('lg')) return;

  if (menuNode.childCount > 0) {
    activeNode.value = [menuNode.id];
    open();
    setCategory([menuNode]);
    return;
  }

  if (category.value !== null) category.value = null;
};

const handleFirstTouch = (menuNode: CategoryTreeItem) => {
  tappedCategories.value.set(menuNode.id, true);
  onCategoryMouseEnter(menuNode);
};

const onCategoryTap = (menuNode: CategoryTreeItem) => {
  if (menuNode.childCount > 0 && isTouchDevice.value && !tappedCategories.value.get(menuNode.id)) {
    return handleFirstTouch(menuNode);
  }

  router.push(localePath(generateCategoryLink(menuNode)));
};

onMounted(() => {
  isTouchDevice.value = 'ontouchstart' in window || navigator.maxTouchPoints > 0;
  removeHook = router.afterEach(() => close());
});

onBeforeUnmount(() => removeHook?.());

watch(
  () => props.categories,
  (categories: CategoryTreeItem[]) => {
    categoryTree.value = categoryTreeGetters.getTree(categories);
    setCategory(categoryTree.value);
  },
);

setCategory(categoryTree.value);

useTrapFocus(
  computed(() => megaMenuReference.value?.[0]),
  trapFocusOptions,
);

useTrapFocus(drawerReference, trapFocusOptions);
</script>
