<template>
  <div class="profile-page">
    <section class="section-profile-cover section-shaped my-0">
      <div class="shape shape-style-1 shape-primary shape-skew alpha-4"></div>
    </section>
    <section class="section section-skew">
      <div class="container">
        <card shadow class="px-5 px-lg-5 card-profile mt--300" no-body>
          <!--상담일지목록 시작-->
          <div class="wrap_content col col-lg-12 p-5">
            <div class="survey-card">
              <h3 class="col-lg-10">
                <div class="text-muted text-left mb-3">
                  <b>문진표</b>
                  <!-- <input type="radio" id="1" value="2"> -->
                </div>
              </h3>

              <!--문진표 start-->
              <div class="question-card" v-for="(question, i) in data" :key="i">
                <div class="question">
                  <b> Q{{ question.number }}. {{ question.title }} </b>
                </div>
                <div class="object_answer row col-lg-12 mt-3 py-3">
                  <!-- <p class="lead">
                    <input
                      style="cursor:pointer"
                      type="radio"
                      :id="question.object_answers[0]+i"
                      v-model="answer[i]"
                      :value="{
                        'options': question.object_answers[0][0],
                        'score': Number(question.object_answers[0][1])
                      }"
                      @change="qwer(Number(question.object_answers[0][1]))"
                       name="radio_answer"
                    />
                    <label for="radio" class="score">
                      {{ question.object_answers[0][1] }}</label
                    >
                    <label class="lead" :for="question.object_answers[0]+i" style="cursor:pointer">{{ question.object_answers[0][0] }}</label>
                  </p>
                  <p class="lead">
                    <input
                      style="cursor:pointer"
                      type="radio"
                      :id="question.object_answers[1]+i"
                      v-model="answer[i]"
                      :value="{
                        'options': question.object_answers[1][0],
                        'score': Number(question.object_answers[1][1])
                      }"
                      @change="qwer(Number(question.object_answers[1][1]))"
                      name="radio_answer"
                    />
                    <label for="radio" class="score">
                      {{ question.object_answers[1][1] }}</label
                    >
                    <label class="lead" :for="question.object_answers[1]+i" style="cursor:pointer">{{ question.object_answers[1][0] }}</label>
                  </p>
                  <p class="lead">
                    <input
                      style="cursor:pointer"
                      type="radio"
                      :id="question.object_answers[2]+i"
                      v-model="answer[i]"
                      :value="{
                        'options': question.object_answers[2][0],
                        'score': Number(question.object_answers[2][1])
                      }"
                      @change="qwer(Number(question.object_answers[2][1]))"
                      name="radio_answer"
                    />
                    <label for="radio" class="score">
                      {{ question.object_answers[2][1] }}</label
                    >
                    <label class="lead" :for="question.object_answers[2]+i" style="cursor:pointer">{{ question.object_answers[2][0] }}</label>
                  </p>
                  <p class="lead">
                    <input
                      style="cursor:pointer"
                      type="radio"
                      :id="question.object_answers[3]+i"
                      v-model="answer[i]"
                      :value="{
                        'options': question.object_answers[3][0],
                        'score': Number(question.object_answers[3][1])
                      }"
                      @change="qwer(Number(question.object_answers[3][1]))"
                      name="radio_answer"
                      checked
                    />
                    <label for="radio" class="score">
                      {{ question.object_answers[3][1] }}</label
                    >
                    <label class="lead" :for="question.object_answers[3]+i" style="cursor:pointer">{{ question.object_answers[3][0] }}</label>
                  </p>
                  <p class="lead">
                    <input
                      style="cursor:pointer"
                      type="radio"
                      :id="question.object_answers[4]+i"
                      v-model="answer[i]"
                      :value="{
                        'options': question.object_answers[4][0],
                        'score': Number(question.object_answers[4][1])
                      }"
                      @change="qwer(Number(question.object_answers[4][1]))"
                      name="radio_answer"
                    />
                    <label for="radio" class="score">
                      {{ question.object_answers[4][1] }}</label
                    >
                    <label class="lead" :for="question.object_answers[4]+i" style="cursor:pointer">{{ question.object_answers[4][0] }}</label>
                  </p> -->
                  <div
                    v-for="(object_answer, j) in question.object_answers"
                    :key="j"
                  >
                    <div class="row mx-3">
                      <p class="lead">
                        <input
                          style="cursor:pointer"
                          type="radio"
                          :name="i"
                          :id="question.object_answers[j]+i"
                          v-model="answer[i]"
                          :value="{
                            'options': object_answer[0],
                            'score': object_answer[1]
                          }"
                        />
                        <label for="radio" class="score">
                          {{ object_answer[1] }}</label
                        >
                        <label class="lead" :for="question.object_answers[j]+i" style="cursor:pointer">{{ object_answer[0] }}</label>
                      </p>
                    </div>
                  </div>
                </div>
              </div>
              <!--문단표 end-->
              <div class="justify-content-center text-center my-5">
                <base-button block type="default" @click="onSubmit">
                  <b class="submit">완료</b>
                </base-button>
              </div>
            </div>
          </div>
        </card>
      </div>
    </section>
  </div>
</template>

<script>
import survey from "./survey.json";
import axios from 'axios'

const data = survey;

export default {
  data() {
    return {
      data,
      answer: [],
      // result: [0, 0, 0]
    };
  },
  methods: {
    onSubmit() {
      const newAnswer = this.answer.filter((x, i) => x != null)
      if (newAnswer.length === 23) {
        // for (let i = 0; i < 23; i++) {
        //   if (i < 13) {
        //     result[0] += Number(this.answer[i][2]);
        //   } else if (i < 21) {
        //     result[1] += Number(this.answer[i][2]);
        //   } else {
        //     result[2] += Number(this.answer[i][2]);
        //   }
        // }
        alert("문진표가 제출되었습니다.");
        axios({
          url: 'https://i7a606.q.ssafy.io/service-api/answer',
          method: 'post',
          data: {
            child_id: this.$route.params.childId,
            answer: this.answer
          }
        })
          .then(res => {
            console.log(res.data)
          })
          .catch(err => {
            console.log(err.response)
          })
        this.$router.push({ name: "children" });
      } else {
        alert("작성 안된 항목이 있습니다.");
      }
    },
  },
  created() {
    console.log(this.$route.params.childId)
  }
};
</script>

<style scoped>
.lead {
  margin: 0;
  font-size: 1rem;
}
.score {
  visibility: hidden;
}
.question-card {
  padding: 15px 10px;
}
.object_answer {
  border: 1px solid #dcdcdc;
}
.submit {
  font-size: 1.5rem;
}
/* .survey-card {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.survey-title {
  display: flex;
  justify-content: center;
  margin-bottom: 2rem;
}
.question {
  background-color: rgb(255, 189, 83);
  padding: 2rem 0 2rem 2rem;
  width: 80rem;
}
.object_answer {
  display: flex;
  justify-content: space-around;
  background-color: rgb(255, 233, 172);
  padding: 1rem 0 1rem 0;
}
.submit {
  background-color: rgb(255, 111, 0);
  border-radius: 10px;
  font-size: 2rem;
  margin-top: 1rem;
  position: absolute;
  left: 85%;
  padding: 4px;
} */
</style>
