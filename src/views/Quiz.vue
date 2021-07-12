<template>
  <div class="quiz">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    
    <h2>QUIZ APP</h2>

    <div class="questions">
      <div v-for="(q, i) in quizData" class="quest" :key="i" :data-level="i">
        <div class="cenas" v-if="qNumber == i">
          <p>{{quizData[qNumber].question}}</p>
          <form>
          
              <label for="a">
              <input type="radio" name="quizAns" class="form-control" id="a" @change="check($event)" @click="answer(i,'a')">
              {{quizData[qNumber].a}}</label>
           
              <label for="b">
              <input type="radio" name="quizAns" class="form-control" id="b" @click="answer(i,'b')">
              {{quizData[qNumber].b}}</label>
            
              <label for="c">
              <input type="radio" name="quizAns" class="form-control" id="c" @click="answer(i,'c')">
              {{quizData[qNumber].c}}</label>
            
              <label for="d">
              <input type="radio" name="quizAns" class="form-control" id="d" @click="answer(i,'d')">
              {{quizData[qNumber].d}}</label>
            
          </form>
          <button @click="resp(i)" class="sub">Submit</button>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data(){
    return {
      qNumber: 0,
      className: '',
      quest: 'quest',
      ans: '',
      quizData: [
        {
          question: '1. Nullam sem diam, condimentum vitae accumsan in, suscipit vitae lacus.',
          a: 'Lorem ipsum dolor sit amet,',
          b: 'consectetur adipiscing elit.',
          c: 'Nam sit amet libero dapibus,',
          d: 'pretium turpis id,',
          correct: 'c',
          answer: '',
        },
        {
          question: '2.Etiam sollicitudin viverra dolor, id posuere velit rutrum et.',
          a: 'consectetur adipiscing elit.',
          b: 'Lorem ipsum dolor sit amet,',
          c: 'pretium turpis id,',
          d: 'Nam sit amet libero dapibus,',
          correct: 'a',
          answer: '',
        },
        {
          question: '3.Integer pulvinar ultricies porttitor.',
          a: 'Nam sit amet libero dapibus,',
          b: 'pretium turpis id,',
          c: 'Lorem ipsum dolor sit amet,',
          d: 'consectetur adipiscing elit.',
          correct: 'd',
          answer: '',
        },
        {
          question: '4.Donec facilisis nulla dolor, congue imperdiet tellus ullamcorper et.',
          a: 'consectetur adipiscing elit.',
          b: 'Nam sit amet libero dapibus,',
          c: 'pretium turpis id,',
          d: 'Lorem ipsum dolor sit amet,',
          correct: 'b',
          answer: '',
        }
      ]
    }
  },
  methods: {
    answer(i, a){
      this.ans = a;
      console.log(this.ans);
      this.quizData[i].answer = this.ans;
    },
    resp(i){
      if(this.quizData[i].answer == this.quizData[i].correct){
       alert('Correto');
       if(this.qNumber < 4){
        this.qNumber++;
        this.className = 'active'+qNumber;
        } 
        if(this.qNumber >= 4){
          alert('');
        }
      } else {
        alert('Errado');
        if(this.qNumber < 4){
          this.qNumber++;
          this.className = 'active'+qNumber;
        } 
        if(this.qNumber >= 4){
          alert('');
        }
      }
      
      
    }
  },
  components: {
    // HelloWorld
  }
}
</script>

<style>

*{
  box-sizing:border-box;
}
.questionList {
    max-width: 100%;
    padding: 20px 10px;
    margin: 0 auto;
    list-style: none;
    width: 100%;
    border-top: 1px solid #eaeaea;
}
.questionList li {
  display:flex;
  justify-content:flex-start;
  align-items:center;
  padding:10px;
  margin-bottom:10px;
}
.sub {
    background-color: #0cbaba;
    background-image: linear-gradient(315deg, #0cbaba 0%, #380036 74%);
    width: 100%;
    padding: 20px;
    font-size: 1em;
    text-transform: uppercase;
    color: #fff;
    font-weight: 900;
    letter-spacing: 2px;
    border: none;
    border-radius: 0 0 10px 10px;
}
.questionList li.done .title {
    text-decoration: line-through;
}
.cenas {
    width: 420px;
    padding: 0;
    border-radius: 10px;
    box-shadow: 0px 3px 10px 6px rgb(0 0 0 / 15%);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    margin-bottom: 30px;
}
.questions {
      display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
label {
    margin-left: 15px;
    width: 100%;
    display: flex;
    justify-content: flex-start;
    margin: 10px 10px 20px;
}
p {
    float: left;
    width: 100%;
    text-align: left;
    font-size: 1em;
    padding: 0 15px;
}
.red {text-decoration:;background-color:red;cursor:pointer;color:#fff;padding:10px 20px;border-radius:10px;}
</style>