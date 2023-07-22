<script>
  // let url;
  // let title;
  export let active1='';
  export let active2='';
  export let active3;
  export let showData;
  export let handleSubmit;
  let brand='';
  let carDetails={};
  console.log("data",showData)

 
</script>

<form action="" class={`z-10 ${active1}`}>
    <h1 class="text-zinc-900 text-3xl pb-3"><b>Add your car Details</b></h1>
    <input type="text"  class="text-black mb-2 w-80 px-2 py-2 rounded-md" placeholder="Company Name" bind:value={carDetails.cName}><br/>
    <input type="text" class="text-black mb-2  w-80 px-2  py-2 rounded-md" placeholder="Enter Image Url" bind:value={carDetails.url}><br/>
    <input type="text"  class="text-black mb-2 w-80 px-2 py-2 rounded-md" placeholder="Enter Title" bind:value={carDetails.title}><br/>
    <input type="text"  class="text-black mb-2 w-80 px-2  py-2 rounded-md" placeholder="Description" bind:value={carDetails.description}><br/>
    
    <button class="bg-blue-400  w-60 rounded-lg p-3" on:click={()=>handleSubmit(carDetails)}>Add Item</button>
</form>
<form action="" class={`z-10 ${active2}`}>
    <h1 class="text-zinc-900 text-3xl pb-3"><b>Add Car Brand</b></h1>
    <input type="text"  class="text-black mb-2 w-60 px-2 p-1 rounded-md" bind:value={brand} placeholder="Add your fav car brand"><br/>
   
    
    <button class="bg-blue-400  w-40 rounded-lg p-3" on:click={()=>handleSubmit(brand)}>Add Brand</button>
</form>

<div
  class={`block rounded-lg bg-white shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700 w-90 ${active3}`}>
  <div
    class="relative overflow-hidden bg-cover bg-no-repeat"
    data-te-ripple-init
    data-te-ripple-color="light">
    <img
      class="rounded-t-lg w-full relative z-10"
      src={showData.url}
      alt=""/>
    <a href="#!">
      <div
        class="absolute bottom-0 left-0 right-0 top-0 h-full w-full overflow-hidden bg-[hsla(0,0%,98%,0.15)] bg-fixed opacity-0 transition duration-300 ease-in-out hover:opacity-100"
      />
    </a>
  </div>
  <div class="p-6">
    <h5
      class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50 capitalize"
    >
      {showData.title}
    </h5>
    <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
      {showData.description}
    </p>
  </div>
</div>

<style>
</style>
