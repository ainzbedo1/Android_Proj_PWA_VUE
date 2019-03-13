<script>
export default {
  name: "Modal",
  data() {
    return {
      previous: null,
      current: '',
      result: '',
      counter: 0
    }
  },
  methods: {
    close() {
      this.$emit("close");
    },
    clear() {
      this.current = '';
      this.result = '';
    },
    append(number) {
      this.counter++;
      var letter = "";
      if(number == 4) letter = "A";
      else if(number == 3.5) letter = "B+";
      else if(number == 3) letter = "B";
      else if(number == 2.5) letter = "C+";
      else if(number == 2) letter = "C";
      else if(number == 1) letter = "D";
      else if(number == 0) letter = "F/FD";

      if(this.current.length == 0) {
          this.current = `${letter}`;
          this.previous = parseFloat(number);
      }
      else{
          this.current = `${this.current}, ${letter}`;
          this.previous = parseFloat(this.previous) + parseFloat(number);
      } 
    },
    equal() {
      var sum = parseFloat(this.previous) / this.counter;
      this.result = sum.toFixed(2);
      this.previous = null;
      this.counter = 0;
    }
  }
};
</script>

<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal">
        <div class="close-modal" >
          <button type="button" class="btn-green" @click="close">
                &times;
            </button>
      </div>
        <div class="calculator">
            <div class="udisplay">{{result || '0'}}</div>
            <div class="display">{{current || '0'}}</div>
            <div @click="append('4')" class="btn">A</div>
            <div @click="append('3.5')" class="btn">B+</div>
            <div @click="append('3')" class="btn">B</div>
            <div @click="append('2.5')" class="btn">C+</div>
            <div @click="append('2')" class="btn">C</div>
            <div @click="append('1')" class="btn">D</div>
            <div @click="append('0')" class="btn">F/FD</div>
            <div @click="clear" class="btn">&#8635;</div>
            <div @click="equal" class="btn operator">=</div>
        </div>
      </div>
    </div>
  </transition>
</template>

<style scoped>
.close-modal{
    position: fixed;
    z-index: 30;
    margin-left: 200px;
    margin-top: -275px;
}
.modal-fade-enter,
.modal-fade-leave-active {
  opacity: 0;
}
.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.5s ease;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  flex-direction: row;
  align-items:center;
  justify-content:center;
}
.modal-header,
.modal-footer {
  padding: 5px;
  text-align: center;
}
.modal-footer {
  border-top: 1px solid #eeeeee;
  justify-content: flex-end;
}

.btn-green {
  position: relative; 
  z-index: 30;
  color: white;
  background: #41b883;
  border-color: #41b883;
  border-bottom-color: #41b883;
  border-radius: 20px;
  margin: 5px;
  font-size: 35px;
}
.input {
  margin-top: 5px;
}
.added-text {
  margin-block-end: -10px;
  margin-block-start: 0.5rem;
}


.calculator {
  margin: 0 auto;
  width: 400px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(100px, auto);
}
.display {
  font-size: 25px;
  grid-column: 1 / 4;
  background-color: #41b883;
  color: #35495e;
  line-height: 80px;
}
.udisplay {
  font-size: 45px;
  grid-column: 1 / 4;
  background-color: #41b883;
  color: #35495e;
  line-height: 120px;
}

.btn {
  font-size: 25px;
  background-color: #35495e;
  color: white;
  line-height: 120px;
}
.operator {
  background-color: #41b883;
  color: white;
}
</style>