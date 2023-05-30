<template>
  <div>
    <form @submit.prevent="saveData">
      <div class="input-area">
        <textarea type="text" :placeholder="placeholder" @input="handleChange" 
        @focus="isShow = true" @blur="handleBlur" v-model="inputText" 
        :readonly="isReadOnly" :maxlength="limitCount" ref="textArea"
        :disabled="inputDisabled"
        />
        <span class="chars-counter">{{ remainingCharsCount }}</span>
      </div>
      <button class="save-btn" v-if="isShow && !isReadOnly" type="submit" :disabled="isDisabled">Save</button>
    </form>
  </div>
</template>

<script>
  export default {
    props: {
      inputLimit: Object,
      inputControl: Object,
    },

    data() {
      return {
        inputText:'',
        inputcheck: null,
        isShow: false,

        // 글자수 제한 props
        limitCount: this.inputLimit.limitCount,
        remainingCharsCount: this.inputLimit.remainingCharsCount,

        // inputControl props
        isReadOnly: this.inputControl.isReadOnly,
        inputDisabled: this.inputControl.isDisabled,
        placeholder: this.inputControl.placeholder,
        
        // button disabled제어
        isDisabled: true,
        saveText: '',
      }
    },
    watch:{
      inputText(newVal,oldVal) {
        if(newVal !== oldVal && this.inputText.length > 0) { 
          this.isDisabled = false;
        } else {
          this.isDisabled = true;
        }
        
        // 저장된 값이랑 같을 경우
        if(newVal === this.saveText) {
          this.isDisabled = true;
        }
      }
    },
    methods: {
      handleChange(event) {
        this.inputText = event.target.value;
        this.remainingCharsCount = this.limitCount - event.target.value.length;
        this.inputcheck = this.inputText.substring(0,this.inputText.length - 1);
      },

      handleBlur() {
        if(this.isDisabled) {
          this.isShow = false;
        }
      },

      saveData() {
        if(confirm('텍스트를 저장하시겠습니까?')) {
          this.inputText = this.$refs.textArea.value;
          this.saveText = this.$refs.textArea.value;
          this.isShow = false;
          this.isDisabled = true;
        }
      }
    }
  }
</script>

<style scoped>
form {
  padding:20px 0;
  display: flex;
  justify-content: center;
}
form .save-btn {
  border: 1px solid #1f80fd;
  box-sizing: border-box;
  border-radius: 6px;
  color: #593af8;
  padding: 10px;
  margin-left: 5px;
  background-color: transparent;
  cursor: pointer;
}
form .save-btn:disabled {
  border: 1px solid #c8c8c8;
  color: #c8c8c8;
  cursor: not-allowed;
}
.input-area {
  width: 89.33%;
  position: relative;
}
.input-area > textarea {
  width: 100%;
  height: 100%;
  font-size: 12px;
  box-sizing: border-box;
  padding: 10px;
  resize: none;
  min-height: 80px;
  margin-right: 5px;
}

.input-area > textarea::placeholder {
  color:inherit;
}
.input-area > textarea:disabled {
  cursor: not-allowed !important;
  background-color: #efefef4d !important;
  border: 1px solid #ccc !important;
  color: #ccc !important;
}
.input-area > textarea:read-only {
  cursor: default;
  background-color: #000;
  color:#fff;
}
.input-area > textarea:read-only:focus {
  outline: none;
}
.input-area .chars-counter {
  position: absolute;
  bottom: 10px;
  right: 15px;
  font-size: 12px;
  color: #ccc;
  font-weight: 500;
}
</style>