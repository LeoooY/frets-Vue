<template>
  <div id='string'>
    <span class="string-note">{{strNoteCode}}</span>
    <div class="string-segment" v-for="(el,idx) in 16" :key="idx" @click="changeBase(segNotes[idx])">
      <span>{{segNotes[idx] }}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'string',
    props: ['stringNote'],
    data() {
      return {
        NOTE_DIFFS: [2, 1, 2, 2, 1, 2, 2],
        segNotes:[]
      }
    },
    computed: {
      strNoteCode: function () {

        return this.stringNote.charCodeAt();
      },
      
    },
    methods: {
      changeBase: function (segNote) {

        this.$emit('changeBase', segNote);

      },
      handleSegNote:function(){
        let segNoteCode=this.strNoteCode;
        // this.segNote.push(segNoteCode);
        let diff;
        for(let i=1; i<16;i++){
          if(segNoteCode>71){
            segNoteCode=65;
          }
          diff=this.NOTE_DIFFS[(segNoteCode-65)%7];
          if(diff%2===1){
            this.segNotes.push(String.fromCharCode(segNoteCode))
            
          }else{
            this.segNotes.push(String.fromCharCode(segNoteCode))
            this.segNotes.push(`#`+String.fromCharCode(segNoteCode))
            
          }
          segNoteCode++
          
        }
      }
    },
    created () {
      this.handleSegNote()
    }
  }
</script>

<style scoped>
  #string {
    display: flex;
  }

  .string-note {
    width: 20px;
    color: #cacaca;
    line-height: 40px;
    margin-right: 10px;
  }


  .string-segment {
    display: inline-block;
    flex: 1;
    height: 40px;
    background: linear-gradient(transparent 18px, #ddd 18px, #ddd 22px, transparent 22px);
  }

  .string-segment:hover {
    cursor: pointer;
    background: linear-gradient(transparent 18px, rgba(252, 126, 16, 0.6) 18px, rgba(252, 126, 16, 0.6) 22px, transparent 22px);
    /* background:rgba(252,126,16,0.6); */
  }

  .string-segment::after {
    content: "";
    display: block;
    height: 40px;
    width: 1px;
    background-color: #ddd;
    float: right;
    margin-top: 20px;
  }
</style>