<script>
    import "../routes/styles.css";
    import Forms from "./Forms.svelte";
    export let showModal=true;
    export let displayModal;
    export let handleSet;
    console.log(displayModal)
    let active1=displayModal=='car'?'':'hidden';
    let active2=displayModal=='brand'?'':'hidden';
    let active3=displayModal!='car' && displayModal!='brand' ? '' : 'hidden';
    let isPromo=true
</script>

{#if showModal }
<div class="backdrop" class:promo={isPromo} >
    <div class="modal">
        <div class={`flex justify-between`}>
            <h1 class={`text-black text-1xl items-center`}><b class={active3}>More about your car</b></h1>
            <i class=" flex fa fa-close text-black justify-end text-2xl cursor-pointer" on:click></i>

        </div>
        <Forms active1={active1} active2={active2} active3={active3} showData={displayModal} handleSubmit={(item='')=>handleSet(item)}/>
    </div>
</div>
{/if}


<style>
    .backdrop{
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.8);
        z-index: 20;
    }

    .modal{
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 180px auto;
        text-align: center;
        align-items: center;
        justify-content: center;
        background: white;
        z-index: 90;
    }

    .promo .modal{
        background: rgb(227, 217, 219);
        color: white;
    }
</style>