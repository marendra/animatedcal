<script>
    import { InlineCalendar } from 'svelte-calendar';
    import { fly } from 'svelte/transition'
    import { onMount } from 'svelte';
    import { backOut } from 'svelte/easing'
    let innerWidth = 1024
    let animate=false
    let waktu =null

    onMount(async () => {
       animate=true
    });

    let resize = innerWidth/2
    let stringResize = resize.toString() + "px"
    const theme = {
        calendar: {
            width: stringResize,
            shadow: '0px 0px 5px rgba(0, 0, 0, 0.25)'
        }
    };
</script>
<svelte:window bind:innerWidth />

<div class=" flex flex-col">

    <div class="flex flex-row align-middle items-center">
        {#if animate}
        <div class="w-1/2"  in:fly={{
          y:-200,
            duration:1500,
            easing:backOut
        }}
        >
            <InlineCalendar bind:waktu {theme}/>
        </div>

        <div class="w-1/2"
        in:fly={{
          y:200,
            duration:1500,
            easing:backOut
        }}
        >
        <img src="orang.png" class="h-screen" />

        </div>
            {/if}
    </div>

</div>

