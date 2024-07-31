<template>
    <div class="w-full">
        <div class="w-full p-[20px] text-[32px] font-bold text-center bg-[#12cbc4] text-[#fff] box-border">
            {{ results[resultIndex].title }}</div>
        <div class="border border-solid border-[#8e959f] p-[20px] text-[18px] w-full bg-[#fff] transition-all duration-[0.4s] ease-linear text-center">
            {{ results[resultIndex].desc }}
        </div>
    </div>
</template>

<script>
export default{
    name:"Result",
    props:['results',"totalCorrect"],
    computed:{
       resultIndex(){
        let index = 0;

        this.results.forEach((e ,i) => {
            if(e.min <= this.totalCorrect && e.max >= this.totalCorrect){
               index= i; 
            }
        });

        return index;
       } 
    }
}

</script>

