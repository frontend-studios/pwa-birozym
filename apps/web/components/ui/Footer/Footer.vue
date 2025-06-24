<template>
  <footer>
    <div class="max-w-screen-3xl mx-auto px-6 lg:px-10 md:py-6 pb-5 md:pb-10">
      <div class="flex flex-wrap justify-center">
        <div class="custom-logo py-5 xl:py-10">
          <NuxtLink :to="localePath(paths.home)" :aria-label="t('goToHomepage')" class="">
            <UiVsfLogo />
          </NuxtLink>
        </div>
      </div>
      <div class="flex flex-wrap justify-around md:justify-between mx-auto xl:max-w-[50%]">
        <div class="flex items-center">
          <SfIconCheck size="sm" class="check mr-1 font-bold" />
          <span class="font-semibold">Top Preise</span>
        </div>
        <div class="flex items-center">
          <SfIconCheck size="sm" class="check mr-1 font-bold" />
          <span class="font-semibold">Gleichbleibende hochwertige Qulität</span>
        </div>
        <div class="flex items-center">
          <SfIconCheck size="sm" class="check mr-1 font-bold" />
          <span class="font-semibold">Bester Service</span>
        </div>
      </div>

      <div class="flex justify-center max-w-64 mx-auto py-5 xl:py-10">
        <div class="social-item">
          <a href="" target="_blank">
            <div class="p-3">
              <span class="font-bold flex items-center justify-center"
                ><SfIconFacebook alt="Facebook" size="base" />
              </span>
            </div>
          </a>
        </div>
        <div class="social-item test-push">
          <a href="" target="_blank">
            <div class="p-3">
              <span class="font-bold flex items-center justify-center"
                ><SfIconYoutube alt="Youtube" size="base" />
              </span>
            </div>
          </a>
        </div>
        <div class="social-item">
          <a href="" target="_blank">
            <div class="p-3">
              <span class="font-bold flex items-center justify-center"
                ><SfIconInstagram alt="Instagram" size="base" />
              </span>
            </div>
          </a>
        </div>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-5 lg:gap-10">
        <div class="payment">
          <div class="pb-2 font-semibold text-lg text-center md:text-left">Bequem bezahlen</div>
          <div class="grid grid-cols-3 gap-2 items-center">
            <img src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Paypal.png" alt="PayPal" />
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/AmazonPay.png"
              alt="AmazonPay"
            />
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/mastercard.png"
              alt="MasterCard"
            />
            <img src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/visa.png" alt="Visa" />
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Rechnung.png"
              alt="Rechnung"
            />
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Vorkasse.png"
              alt="Vorkasse"
            />
          </div>
        </div>
        <div class="delivery">
          <div class="pb-2 font-semibold text-lg text-center md:text-left">Versandoption</div>
          <div class="flex items-center justify-center md:grid gap-2 md:grid-cols-3 mb-4">
            <img src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/DHL.png" alt="DHL" />
          </div>
          <ul class="list-disc text-sm list-inside">
            <li>Schneller Versand ab 55 €</li>
            <li>Versand mit DHL Express-Versand möglich</li>
            <li>Versandfertig in 24h</li>
          </ul>
        </div>
        <div class="savety">
          <div class="pb-2 font-semibold text-lg text-center md:text-left">Kauf ohne Risiko</div>
          <div class="flex items-center justify-center md:grid gap-2 md:grid-cols-4 mb-4 security min-h-20">
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Trust.png"
              alt="Käuferschutz & Datenschutz"
            />
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Trusted-icon.png"
              alt="Sichere SSL-Verschlüsselung"
            />
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Honesty.png"
              alt="Widerrufsrecht"
            />
          </div>
          <ul class="list-disc text-sm list-inside">
            <li>Käuferschutz & Datenschutz</li>
            <li>Sichere SSL-Verschlüsselung</li>
            <li>Widerrufsrecht</li>
          </ul>
        </div>

        <div class="rating">
          <div class="pb-2 font-semibold text-lg text-center md:text-left">Bewertung</div>
          <div class="flex items-center min-h-20">
            <img
              src="https://cdn02.plentymarkets.com/xetuu6ddej5k/frontend/birozym/footer/Ausgezeichnet.png"
              alt="Ausgezeichnet.org Bewertungen"
              class=""
            />
            <div class="text-xs ml-2">
              <div>
                <div>
                  <SfIconStarFilled size="sm" class="text-primary-900" />
                  <SfIconStarFilled size="sm" class="text-primary-900 -ml-1" />
                  <SfIconStarFilled size="sm" class="text-primary-900 -ml-1" />
                  <SfIconStarFilled size="sm" class="text-primary-900 -ml-1" />
                  <SfIconStarFilled size="sm" class="text-primary-900 -ml-1" />
                </div>
                <span class="font-semibold text-sm">4,8</span>/5, basierend auf
                <span class="font-semibold text-sm">19.512</span> Bewertungen
              </div>
              <a
                href="https://www.google.com/search?sca_esv=3d6848995d8cd9b4&rlz=1C1CHBD_deDE892DE892&tbm=lcl&sxsrf=AHTn8zra5aAkQiN_OMOl8LAGlBmVTUD8gQ:1742562473685&q=Superwurm+GmbH+%26+Co.+KG+Rezensionen&rflfq=1&num=20&stick=H4sIAAAAAAAAAONgkxI2tjQzMTQxMza3BFImhqYGBkYbGBlfMSoHlxakFpWXFuUquOcmeSioKTjn6yl4uysEpVal5hVn5uel5i1iJUYVAKmEYxNmAAAA&rldimm=3964146379414415002&hl=de-DE&sa=X&ved=2ahUKEwiOv_iJn5uMAxU1zQIHHUUWJeMQ9fQKegQIRBAF&biw=1920&bih=945&dpr=1#lkt=LocalPoiReviews"
                class="underline"
                target="_blank"
                >Zu den Bewertungen</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
  <div class="sub-footer pb-20 md:pb-0 bg-primary-500">
    <div class="max-w-screen-3xl mx-auto px-6 lg:px-10 md:py-6 pt-5 md:pt-10">
      <div class="mx-auto flex flex-wrap justify-around md:justify-between" data-testid="section-top">
        <a href="/contact/" class="m-0 text-xs text-white">Kontakt</a>
        <a href="/privacy-policy/" class="m-0 text-xs text-white">Datenschutz</a>
        <a href="/terms-and-conditions/" class="m-0 text-xs text-white">AGB</a>
        <a href="/legal-disclosure/" class="m-0 text-xs text-white">Impressum</a>
        <a href="/zahlung-versand/" class="m-0 text-xs text-white">Zahlung & Versand</a>
        <a href="/cancellation-rights/" class="m-0 text-xs text-white">Widerrufsrecht - und Formular</a>
        <a href="/rueckgabe-reklamation/" class="m-0 text-xs text-white">Rückgabe & Reklamation</a>
      </div>

      <div class="text-center py-10">
        <p class="text-white text-sm">© Biomenta GmbH</p>
      </div>

      <div class="copyright text-white text-xs text-center">
        <p>
          * Alle Preise verstehen sich inkl. MwSt. zzgl. Versandkosten. Alle Angebote sind freibleibend zzgl.
          Versandkosten und bei Nachnahme Übermittlungsentgelt. Irrtümer, Druckfehler und Preisänderungen
          vorbehalten.<br />
          Umsetzung:
          <a href="https://www.frontend-studios.de" rel="nofollow" class="underline">Frontend Studios GmbH</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import {
  SfLink,
  SfListItem,
  SfIconFacebook,
  SfIconYoutube,
  SfIconInstagram,
  SfIconCheck,
  SfIconStarFilled,
} from '@storefront-ui/vue';
import { categories } from '~/mocks';
import type { FooterProps } from './types';

import { paths } from '~/utils/paths';
const { t } = useI18n();

const storename: string = useRuntimeConfig().public.storename;

const companyName: string = `© ${storename} ${new Date().getFullYear()}`;

const { simplifiedFooter = false } = defineProps<FooterProps>();

const localePath = useLocalePath();
const NuxtLink = resolveComponent('NuxtLink');
</script>
