<script>
    import '../routes/styles.css';
    import { items } from './+sidebarItems';
    import Cards from './Cards.svelte';
    import Modal from './model.svelte'
    import { cardData } from './+cardData';

    import { Button, Dropdown, DropdownItem, Chevron } from 'flowbite-svelte'
    let allBrands=items;
    let sidebarItems = allBrands;
    let searchCars;
    let allCars=cardData;
    let filterCars=allCars;
    let cardIndex=0;

    let showModal=false;
    let displayModal=false;
    const toggleModal=(info)=>{
        console.log(info)
        showModal = !showModal;
        if(info=='car' || info=='brand')
            displayModal=info;
        else {
            cardIndex=allCars.findIndex((data)=>data?.title==info.title);
            displayModal=false;
        }
    }

   console.log(displayModal)
    let showCollapse='hidden';
    const handleShow=()=>{
        showCollapse= showCollapse == 'hidden'?"":'hidden';
    }

    const handleSearch=()=>{
        filterCars=allCars.filter((data)=>data.title.toLowerCase().indexOf(searchCars.toLowerCase())>=0);
    }
    const handleFilter=(cModal=null)=>{
            if(cModal!=null)
                filterCars=allCars.filter((data)=>data.cName.toLowerCase().indexOf(cModal.toLowerCase())>=0);
            else {
                filterCars=[...allCars];
                sidebarItems=[...allBrands];
                searchCars='';

            }
    }
    const handleChange=(e)=>{
        console.log(e)
        sidebarItems=allBrands.filter((data)=>data.title.toLowerCase().indexOf(e.target.value.toLowerCase())>=0);
    }
    const handlebrand=(item='')=>{
        console.log(item)
        allBrands=[...items,{title:item}]
        sidebarItems=allBrands;
        toggleModal();
    }
    const handleCar=(item={})=>{
        console.log(item)
        allCars=[...cardData,item]
        filterCars=allCars;
        toggleModal();
    }
</script>
{#if displayModal=='car'}
<Modal on:click={toggleModal} bind:showModal displayModal='car' handleSet={(item='')=>handleCar(item)}>
</Modal>
{:else if displayModal=='brand'}
<Modal on:click={toggleModal} bind:showModal displayModal='brand' handleSet={(item='')=>handlebrand(item)}>
</Modal>
{:else}
<Modal on:click={toggleModal} bind:showModal displayModal={allCars[cardIndex]}>
</Modal>
{/if}


<div class="flex flex-col">
    <div class="flex flex-row  justify-between mx-5px px-5">
        <div class="flex flex-row">
            <i on:click={handleShow} class=" flex fa fa-bars mt-5 mx-2 text-black  cursor-pointer justify-end text-2xl hover:scale-90"></i>
            <button on:click={()=>handleFilter(null)} ><h1 class="text-3xl font-bold mt-2 ml-4  border-gray-500 ">Car World</h1></button>
            <!-- <li class="px-4 mt-5 text-1xl cursor-pointer list-none w-30 rounded-lg p-1" on:click={toggleModal}><b>Add New </b></li>
            <li class="px-4 mt-5 text-1xl cursor-pointer list-none w-30 rounded-lg p-1" on:click={toggleModal}><b>Add New Car</b></li> -->

            <Button class="bg-white text-black pt-5 hover:bg-white border-white focus:ring-0 focus:ring-offset-0"><Chevron>Add New</Chevron></Button>
            <Dropdown class="relative z-20" >
            <DropdownItem on:click={()=>toggleModal('car')}>Add Car</DropdownItem>
            <DropdownItem on:click={()=>toggleModal('brand')}>Add Company</DropdownItem>
            </Dropdown>
            <div>
                <ul>

                </ul>
            </div>
           
        </div>
        <div>
            <input type="text" class="px-4 mt-5 rounded-lg  border-2 border-sky-500  w-80" placeholder="Search..." bind:value={searchCars}/>
            <button class="px-4 text-white rounded-lg bg-gray-600 border-l py-2 hover:bg-gray-500" on:click={handleSearch}>
                Search
            </button>
        </div>
    </div>

    <div class="flex flex-row ">
         <div class={`flex flex-col mt-5 py-4 px-5 min-h-screen bg-cyan-300 w-1/5 h-auto my-scroll ${showCollapse}`}>
            <!-- <h1 class="text-black-600 justify-center items-center font-bold md:text-2xl  sm:text-1xl">Choose Car Brand</h1> -->
            <input type="text" class="px-5 mx-5  rounded-lg py-2 w-29 border-2" placeholder="Search..." on:change={(e)=>handleChange(e)}/>
            
            <ul class="my-4" >
            {#each sidebarItems as item}
                <li class="py-2 px-4 hover:scale-105 cursor-pointer hover:text-orange-500" on:click={()=>handleFilter(item.title)}><b>{item.title}</b></li>
            {/each}
                
                
            </ul>
        
        </div>
        <div>
            <Cards showData={filterCars} handleShow={(item='')=>toggleModal(item)}/>
        </div>
    </div>

</div>

<style>
    .my-scroll{
        align-items: stretch;
        padding:10px 0 30px ;
        transition: 0.5s ease-in-out;
        border-top-right-radius: 13px;
       
    }
    
</style>

