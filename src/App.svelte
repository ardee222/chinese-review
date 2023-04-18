<script>
  import data from "./data.json"
  let testing = false;
  let choose = false;
  let chosen,qus,all,author,title,checked,current_ans,index,correct,worng
  all = data.all
  author = data.author
  title = data.title
  let shuffled_all = all.sort((a, b) => 0.5 - Math.random());
  let correct_ans = []
  let ans_list = []
  $: index = 0;
  $: correct = 0;
  $: wrong = 0;
  $:qus = shuffled_all[index][0]

  $:chosen = false;
  $:checked = false;

  for(let i of shuffled_all){
    correct_ans.push(i[1]+i[2])
  }
  $:current_ans = correct_ans[index]
  
  function creat_list(){
    let a = author.sort((a, b) => 0.5 - Math.random());
    let b = title.sort((a, b) => 0.5 - Math.random());
    let text = a[0]+b[0]
    if(ans_list.length >= 3){
      let correct_ans = {text:shuffled_all[index][1] + shuffled_all[index][2],correct:true}
      if(ans_list.indexOf(correct_ans) === -1 ){ans_list.push(correct_ans)}
      ans_list.sort((a, b) => 0.5 - Math.random());
      console.log(ans_list)
      }else{
      if(ans_list.indexOf(text) === -1){
        ans_list.push({text:text,correct:false})
      }
      $: ans_list = ans_list
      creat_list()
    }
  }

  function check(){
    chosen = true;
    if(this.innerText === current_ans){
      correct++
      checked = true
    }else{
      wrong++
      checked = false;
    }
    index++
    setTimeout(()=>{
    ans_list = []
    creat_list()
    chosen = false;
  },1000)}

  function initial(){
    correct = 0
    wrong = 0
    index = 0
    ans_list = []
  }
  window.onload = ()=>{console.log(current_ans)}
</script>

<main class="relative flex flex-col items-center m-auto max-w-md w-screen h-screen bg-[#94A7AE]">
  <!--main-->
  {#if !testing && !choose}
  <div class="my-10 text-xl">第三段第二次中文測驗温習</div>
  <div class="text-xs border border-b-0 border-x-0 max-w-sm w-screen my-2">
    有bug請見願
  </div>
  <div class="flex flex-col justify-center space-y-8 mt-10">
    <div class="border rounded-lg text-center p-2  text-xl hover:bg-green-300 "
    on:mouseup={()=>{testing = true;creat_list()}}>選擇題</div>
    <div class="border rounded-lg text-center p-2  text-xl hover:bg-green-300 "
    on:mouseup={()=>{choose = true}}>配對</div>
    <div class="border rounded-lg text-center p-2  text-xl hover:bg-green-300 "
    on:mouseup={()=>{choose = true}}>名句續寫</div>
  </div>
  <footer class="absolute right-4 bottom-4">謝卓熹個人財產</footer>
  {/if}

  {#if testing || choose}
  <!--function_list-->
  <div class="mt-4 px-8 w-full flex items-center place-content-between ">
    <div class="hover:bg-green-300 hover:rounded-lg p-2 flex items-center text-xs text-white rounded-lg"
    on:mouseup={()=>{testing = false;choose = false}}>
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
        <path stroke-linecap="round" stroke-linejoin="round" d="M18.75 19.5l-7.5-7.5 7.5-7.5m-6 15L5.25 12l7.5-7.5" />
      </svg>
      <div class="mt-1"
      on:mouseup={initial}
      >back</div>
    </div>

    <div class="flex space-x-4">
      <div>對:{correct}</div>
      <div>錯:{wrong}</div>
      <div>{index+1}/50</div>
    </div>
  </div>

  <div class="border border-x-0 border-b-0 border-t-2 m-2  border-dashed max-w-sm w-screen h-10 p-2 "></div>
  {/if}
  {#if testing}
  <!--question-->
  <div class="flex flex-col items-center space-y-4 text-xl">
    <div class="border rounded-lg truncate p-2">{qus}</div>   
    <div class="space-y-4">
    {#each ans_list as ans}
      <div class="truncate p-2"
      on:mouseup={check}
      class:bg-green-200={chosen === true && ans.correct}
      class:bg-red-200={chosen === true && !ans.correct}
      >{ans.text}</div>
    {/each}
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
