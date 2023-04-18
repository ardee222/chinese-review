<script>
  let testing = false;
  let choose = false;
  
</script>

<main class="relative flex flex-col items-center m-auto max-w-md w-screen h-screen bg-[#94A7AE]">
  <!--main-->
  {#if !testing && !choose}
  <div class="my-10 text-xl">第三段第二次中文測驗温習</div>
  <div class="text-xs border border-b-0 border-x-0 max-w-sm w-screen my-2">
    有bug請見願
  </div>
  <div class="flex flex-col justify-center space-y-5 mt-10">
    <div class="border rounded-lg text-center p-2  text-xl hover:bg-green-300 "
    on:mouseup={()=>{testing = !testing}}>選擇題</div>
    <div class="border rounded-lg text-center p-2  text-xl hover:bg-green-300 "
    on:mouseup={()=>{choose = !choose}}>配對</div>
    <div class="border rounded-lg text-center p-2  text-xl hover:bg-green-300 "
    on:mouseup={()=>{choose = !choose}}>名句續寫</div>
  </div>
  <footer class="absolute right-4 bottom-4">謝卓熹個人財產</footer>

  {/if}

  {#if testing}
  <!--function_list-->
  <div class="mt-4 px-8 w-full flex items-center place-content-between ">
    <div class="hover:bg-green-300 hover:rounded-lg p-2 flex items-center text-xs text-white rounded-lg"
    on:mouseup={()=>{testing = !testing}}>
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
        <path stroke-linecap="round" stroke-linejoin="round" d="M18.75 19.5l-7.5-7.5 7.5-7.5m-6 15L5.25 12l7.5-7.5" />
      </svg>
      <div class="mt-1">back</div>
    </div>

    <div class="flex space-x-4">
      <div>對:</div>
      <div>錯:</div>
      <div>x/50</div>
    </div>
  </div>

  <div class="border border-x-0 border-b-0 border-t-2 m-2  border-dashed max-w-sm w-screen h-10"></div>

  <!--question-->
  <div class="flex flex-col items-center">
    <div class="border w-60 ">
      a
    </div>    
  </div>
  {/if}

  <!--配對-->
  {#if choose}
    <div class="m-auto">
      未整
    </div>
  {/if}
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@900&family=Noto+Sans+TC:wght@500&family=Secular+One&display=swap');
  *{
    box-sizing: border-box;
    font-weight: bold;
    font-family: 'Secular One', sans-serif,'標楷體';
  }
</style>
