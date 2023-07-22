<script>
  import "../routes/styles.css";
  export let showData;
  export let handleShow;
 
</script>

<div class="grid sm:grid-cols-2 md:grid-cols-2 gap-4 sm:px-0 render-img">
  {#each showData as data}
    <div
      class="flex flex-col justify-between items-center rounded-lg mt-5 py-4  border-2  mx-10  h-25 bg-gray shadow-[0_2px_15px_-3px_rgba( 0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-white z-auto"
    >
      <div
        class="relative overflow-hidden bg-cover bg-no-repeat z-auto"
        data-te-ripple-init
        data-te-ripple-color="light"
      >
        <img
          class="rounded-t-lg h-400 w-400"
          src={data.url}
          alt=""
        />
        <a href="#">
          <div
            class="absolute bottom-0 left-50 right-0 top-0 h-full w-full overflow-hidden bg-[hsla(0,0%,98%,0.15)] bg-fixed opacity-0 transition duration-300 ease-in-out hover:opacity-100"
          />
        </a>
      </div>
      <div class="p-6">
        <h5
          class="mb-2 text-xl font-medium leading-tight text-black-400 dark:text-neutral-800 capitalize"
        >
          {data.title}
        </h5>
        <p class="mb-4 text-base text-neutral-600 dark:text-neutral-800">
          {data.description}
        </p>
        <button
          type="button"
          class="inline-block rounded bg-neutral-700 px-6 pb-2 pt-2.5 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_#5c9fcc] transition duration-150 ease-in-out hover:bg-primary-600 hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:bg-primary-600 focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:outline-none focus:ring-0 active:bg-primary-700 active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] dark:shadow-[0_4px_9px_-4px_rgba(59,113,202,0.5)] dark:hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.2),0_4px_18px_0_rgba(59,113,202,0.1)] dark:focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.2),0_4px_18px_0_rgba(59,113,202,0.1)] dark:active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.2),0_4px_18px_0_rgba(59,113,202,0.1)]"
          data-te-ripple-init
          data-te-ripple-color="light"
          on:click={()=>handleShow(data)}
        >
          Show More
        </button>
      </div>
    </div>
  {/each}
</div>

<style>

</style>


