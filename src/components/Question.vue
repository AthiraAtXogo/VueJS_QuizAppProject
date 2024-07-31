<!-- <template>
    <div class=" relative w-full">
        <div class="h-[3.125rem] mt-[.625rem] bg-[#ddd] relative">
            <div class="h-[3.125rem] bg-[#ff6372] transition-all duration-[0.3s] ease-linear"></div>
            <div class="absolute top-[.9375rem] left-0 text-center text-[#fff] w-full">1 out of 3 questions answered</div>
        </div>
        <div class="relative w-full" v-for="(question,qIndex) in questions" :key="question.q" v-show="questionAnswered==qIndex">
           
            <div class=" w-full p-5 text-[2rem] font-bold text-center bg-[#00ca8c] text-[#fff] box-border ">{{question.q}}</div>
           
            <div class="border-solid border border-[#8e959f] p-5 text-[18px] w-full bg-[#fff] transition-all duration-[0.2s] ease-linear ">
                <div class="border-solid border border-[#8e959f] p-5 text-[18px] w-full bg-[#fff] transition-all duration-[0.2s] ease-linear cursor-pointer hover:bg-[#8ce200] hover:border-[#8ce200] hover:text-[#fff] "  v-for="answer in question.answers" 
                :key="answer.text" 
                @click.prevent="selectAnswer(answer.is_correct)">
                {{ answer.text }}</div>
                
            </div>
        </div>
    </div>
</template> -->

<template>
    <div class="relative w-full">
        <div class="h-[3.125rem] mt-[.625rem] bg-[#ddd] relative">
           
            <div class="h-[3.125rem] bg-[#ff6372] transition-all duration-[0.3s] ease-linear" :style="{width:`${(questionAnswer/questions.length)*100}%`}"></div>
            
            <div class="absolute top-[.9375rem] left-0 text-center text-[#fff] w-full">{{ questionAnswer }} out of {{ questions.length }} questions answered</div>
        </div>
        <div class="relative w-full" v-for="(question, qIndex) in questions" :key="question.q" v-show="questionAnswer === qIndex">
            <div class="w-full p-5 text-[2rem] font-bold text-center bg-[#00ca8c] text-[#fff] box-border">{{ question.q }}</div>
           
            <div  class="cursor-pointer">
                <div class="border-solid border border-[#8e959f] p-5 text-[18px] w-full bg-[#fff] transition-all duration-[0.2s] ease-linear hover:bg-[#8ce200] hover:border-[#8ce200] hover:text-[#fff]" v-for="answer in question.answers" :key="answer.text" @click.prevent="selectAnswer(answer.is_correct)">{{ answer.text }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name:"Question",
    props:['questions' , 'questionAnswer'],
    emits:['question-answered'],
    methods:{
        selectAnswer(is_correct){
            this.$emit('question-answered',is_correct)
        }
    }
}

</script>

