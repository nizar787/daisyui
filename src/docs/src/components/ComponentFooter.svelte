<script>
  import { page } from "$app/stores"
  import { currentLang, defaultLang, t } from "$lib/i18n"

  export let pages = []

  function extractPages(obj) {
    const items = []
    function recursiveExtract(obj) {
      if (obj.href) {
        items.push(obj)
      }
      if (obj.items) {
        obj.items.forEach((item) => {
          recursiveExtract(item)
        })
      }
    }
    obj.forEach((item) => {
      recursiveExtract(item)
    })
    return items
  }
  let arrayOfPagesInOrder = extractPages(pages)

  $: currentPageIndex = arrayOfPagesInOrder.findIndex((item) => item.href == $page.url.pathname)
</script>

{#if arrayOfPagesInOrder[currentPageIndex]}
  <div class="not-prose pb-10">
    <div class="bg-base-content/10 mx-1 my-10 h-px" />

    <div class="flex justify-between">
      <div>
        {#if currentPageIndex > 0 && arrayOfPagesInOrder[currentPageIndex - 1]}
          <a
            href={arrayOfPagesInOrder[currentPageIndex - 1].href}
            class="btn btn-sm md:btn-md gap-2 lg:gap-3">
            <svg
              class="h-6 w-6 fill-current md:h-8 md:w-8"
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24">
              <path d="M15.41,16.58L10.83,12L15.41,7.41L14,6L8,12L14,18L15.41,16.58Z" />
            </svg>
            <div class="flex flex-col items-start">
              <span class="text-base-content/50 hidden text-xs font-normal md:block">
                {$t("Prev")}
              </span>
              <span>{$t(arrayOfPagesInOrder[currentPageIndex - 1].name)}</span>
            </div>
          </a>
        {/if}
      </div>
      <div>
        {#if currentPageIndex < arrayOfPagesInOrder.length - 1 && arrayOfPagesInOrder[currentPageIndex + 1]}
          <a
            href={arrayOfPagesInOrder[currentPageIndex + 1].href}
            class="btn btn-neutral btn-sm md:btn-md gap-2 lg:gap-3">
            <div class="flex flex-col items-end">
              <span class="text-neutral-content/50 hidden text-xs font-normal md:block">
                {$t("Next")}
              </span>
              <span>{$t(arrayOfPagesInOrder[currentPageIndex + 1].name)}</span>
            </div>
            <svg
              class="h-6 w-6 fill-current md:h-8 md:w-8"
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24">
              <path d="M8.59,16.58L13.17,12L8.59,7.41L10,6L16,12L10,18L8.59,16.58Z" />
            </svg>
          </a>
        {/if}
      </div>
    </div>

    <div class="bg-base-content/10 mx-1 my-10 h-px" />

    <div class="flex flex-col justify-between gap-2 px-4 text-xs md:flex-row">
      <div class="flex flex-col gap-2">
        <div class="flex items-center gap-2">
          <svg
            class="inline-block h-4 w-4 fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24">
            <path
              fill-rule="evenodd"
              d="M12,23 C5.92486775,23 1,18.0751322 1,12 C1,5.92486775 5.92486775,1 12,1 C18.0751322,1 23,5.92486775 23,12 C23,18.0751322 18.0751322,23 12,23 Z M12,21 C16.9705627,21 21,16.9705627 21,12 C21,7.02943725 16.9705627,3 12,3 C7.02943725,3 3,7.02943725 3,12 C3,16.9705627 7.02943725,21 12,21 Z M12.0003283,16.9983464 C11.4478622,16.9983464 11,16.5506311 11,15.9983464 C11,15.4460616 11.4478622,14.9983464 12.0003283,14.9983464 C12.5527943,14.9983464 13.0006565,15.4460616 13.0006565,15.9983464 C13.0006565,16.5506311 12.5527943,16.9983464 12.0003283,16.9983464 Z M13,14 L11,14 C11,12.2983529 11.6245803,11.5696759 13.0527864,10.8555728 C13.8745803,10.4446759 14,10.2983529 14,9.5 C14,8.556407 13.2771608,8 12,8 C10.8954305,8 10,8.8954305 10,10 L8,10 C8,7.790861 9.790861,6 12,6 C14.2843464,6 16,7.32062807 16,9.5 C16,11.2016471 15.3754197,11.9303241 13.9472136,12.6444272 C13.1254197,13.0553241 13,13.2016471 13,14 Z" />
          </svg>
          <div>
            {$t("Do you have a question?")}
            <a
              target="_blank"
              rel="noopener, noreferrer"
              class="link"
              href="https://github.com/saadeghi/daisyui/discussions">
              {$t("ask the community")}
            </a>
          </div>
        </div>
        <div class="flex items-center gap-2">
          <svg
            class="inline-block h-4 w-4 fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 1792 1792">
            <path
              d="M1696 960q0 26-19 45t-45 19h-224q0 171-67 290l208 209q19 19 19 45t-19 45q-18 19-45 19t-45-19l-198-197q-5 5-15 13t-42 28.5-65 36.5-82 29-97 13v-896h-128v896q-51 0-101.5-13.5t-87-33-66-39-43.5-32.5l-15-14-183 207q-20 21-48 21-24 0-43-16-19-18-20.5-44.5t15.5-46.5l202-227q-58-114-58-274h-224q-26 0-45-19t-19-45 19-45 45-19h224v-294l-173-173q-19-19-19-45t19-45 45-19 45 19l173 173h844l173-173q19-19 45-19t45 19 19 45-19 45l-173 173v294h224q26 0 45 19t19 45zm-480-576h-640q0-133 93.5-226.5t226.5-93.5 226.5 93.5 93.5 226.5z" />
          </svg>
          <div>
            {$t("Do you see a bug?")}
            <a
              target="_blank"
              rel="noopener, noreferrer"
              class="link"
              href={`https://github.com/saadeghi/daisyui/issues?q=${arrayOfPagesInOrder[currentPageIndex].name}`}>
              {$t("open an issue on GitHub")}
            </a>
          </div>
        </div>
        <div class="flex items-center gap-2">
          <svg
            class="inline-block h-4 w-4 fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24">
            <path
              d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z" />
          </svg>
          <div>
            {$t("Do you like daisyUI?")}
            <a
              target="_blank"
              rel="noopener, noreferrer"
              class="link"
              href={`https://twitter.com/intent/tweet?text=daisyUI%20%0D%0AComponents%20for%20Tailwind%20CSS%20%0D%0Ahttps://daisyui.com`}>
              {$t("tweet about it!")}
            </a>
          </div>
        </div>
        <div class="flex items-center gap-2">
          <svg
            class="inline-block h-4 w-4 fill-rose-500"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 512 512">
            <path
              d="M256,448a32,32,0,0,1-18-5.57c-78.59-53.35-112.62-89.93-131.39-112.8-40-48.75-59.15-98.8-58.61-153C48.63,114.52,98.46,64,159.08,64c44.08,0,74.61,24.83,92.39,45.51a6,6,0,0,0,9.06,0C278.31,88.81,308.84,64,352.92,64,413.54,64,463.37,114.52,464,176.64c.54,54.21-18.63,104.26-58.61,153-18.77,22.87-52.8,59.45-131.39,112.8A32,32,0,0,1,256,448Z" />
          </svg>
          <div>
            {$t("Support daisyUI's development")}:
            <a
              target="_blank"
              rel="noopener, noreferrer"
              class="link"
              href={`https://opencollective.com/daisyui`}>
              {$t("Open Collective")}
            </a>
          </div>
        </div>
      </div>
      <div class="flex flex-col gap-2">
        <div class="flex items-center gap-2">
          <svg
            class="inline-block h-4 w-4 fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24">
            <path
              d="M20.71,7.04C21.1,6.65 21.1,6 20.71,5.63L18.37,3.29C18,2.9 17.35,2.9 16.96,3.29L15.12,5.12L18.87,8.87M3,17.25V21H6.75L17.81,9.93L14.06,6.18L3,17.25Z" />
          </svg>
          <div>
            <a
              target="_blank"
              rel="noopener, noreferrer"
              class="link"
              href={`https://github.com/saadeghi/daisyui/blob/master/src/docs/src/routes/(docs)${$page.url.pathname.replace(
                /\/$/,
                ""
              )}/+page.svelte.md?plain=1`}>
              {$t("Edit this page on GitHub")}
            </a>
          </div>
        </div>
        {#if $currentLang != defaultLang}
          <div class="flex items-center gap-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
              class="inline-block h-4 w-4 fill-current">
              <path
                fill-rule="evenodd"
                d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-1.5 0a6.5 6.5 0 11-11-4.69v.447a3.5 3.5 0 001.025 2.475L8.293 10 8 10.293a1 1 0 000 1.414l1.06 1.06a1.5 1.5 0 01.44 1.061v.363a1 1 0 00.553.894l.276.139a1 1 0 001.342-.448l1.454-2.908a1.5 1.5 0 00-.281-1.731l-.772-.772a1 1 0 00-1.023-.242l-.384.128a.5.5 0 01-.606-.25l-.296-.592a.481.481 0 01.646-.646l.262.131a1 1 0 00.447.106h.188a1 1 0 00.949-1.316l-.068-.204a.5.5 0 01.149-.538l1.44-1.234A6.492 6.492 0 0116.5 10z"
                clip-rule="evenodd" />
            </svg>

            <div>
              <a
                target="_blank"
                rel="noopener, noreferrer"
                class="link"
                href={`https://github.com/saadeghi/daisyui/blob/master/src/docs/src/translation/${$currentLang}.json`}>
                {$t("Contribute to translation")}
              </a>
            </div>
          </div>
        {/if}
      </div>
    </div>
  </div>
{/if}

<div
  class="card bg-base-100 from-base-200 not-prose outline-base-content/5 relative overflow-hidden bg-gradient-to-b font-sans shadow-lg outline -outline-offset-1 md:flex-row-reverse">
  <figure class="max-md:bg-primary/10 isolate shrink-0 md:w-2/3">
    <a>
      <img
        class="pointer-events-none"
        alt="daisyUI store"
        src="/images/store/admin-dashboard.png" />
    </a>
  </figure>
  <div
    class="bg-accent -left-1/5 pointer-events-none absolute bottom-[-50%] aspect-square w-3/4 -translate-x-1/2 rounded-full opacity-20 blur-3xl">
  </div>
  <div
    class="bg-primary pointer-events-none absolute bottom-[-120%] left-1/2 aspect-square w-full -translate-x-1/2 rounded-full opacity-20 blur-3xl">
  </div>
  <div
    class="bg-base-100 pointer-events-none absolute -top-3/4 right-1/4 z-[3] aspect-square w-1/2 rounded-full opacity-60 blur-3xl">
  </div>
  <div class="card-body relative isolate z-[3]">
    <h2
      class="card-title text-base-content text-xl font-black contrast-200 [text-wrap:balance] sm:w-[250%] sm:text-2xl md:text-4xl lg:text-3xl xl:text-5xl">
      <span>
        Start your next project
        <span class="italic">even faster</span>
      </span>
    </h2>
    <div class="grow">
      <h2
        class="card-title text-xl font-light sm:w-[250%] sm:text-2xl md:text-3xl lg:text-xl xl:text-3xl">
        <svg
          class="inline h-4 w-4 md:h-6 md:w-6"
          width="32"
          height="32"
          viewBox="0 0 415 415"
          xmlns="http://www.w3.org/2000/svg">
          <rect x="82.5" y="290" width="250" height="125" rx="62.5" fill="#1AD1A5" />
          <circle cx="207.5" cy="135" r="125" fill="white" />
          <circle cx="207.5" cy="135" r="56" fill="#FF9903" />
        </svg>
        with daisyUI Admin Dashboard
      </h2>
    </div>
    <a class="btn btn-block btn-primary group" href="/store">
      More details
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="hidden h-6 w-6 transition-transform duration-300 group-hover:translate-x-1 rtl:rotate-180 rtl:group-hover:-translate-x-1 md:inline-block">
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M17.25 8.25L21 12m0 0l-3.75 3.75M21 12H3">
        </path>
      </svg>
    </a>
  </div>
</div>
