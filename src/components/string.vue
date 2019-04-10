<template>
  <div id='string'>
    <span class="string-note">{{strNoteCode}}</span>
    <div class="string-segment" v-for="(el,idx) in 16" :key="idx" @click="changeBase(segNotes[idx].sup+segNotes[idx].note,idx)">
      <span v-if="rs.indexOf(idx)!==-1">{{segNotes[idx].sup+segNotes[idx].note+segNotes[idx].ncode }}</span>
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
        normalNoteDiff:[2,2,1,2,2,2,1],
        segNotes:[],
        rs:[]
      }
    },
    computed: {
      strNoteCode: function () {

        return this.stringNote.charCodeAt();
      },
      
    },
    methods: {

      changeBase: function (segNote,idx) {
        let temp=idx;
        this.rs=[];
        this.rs.push(temp);
        let len=this.normalNoteDiff.length;

        for(let i=0;i<len;i++){
          
          temp+=this.normalNoteDiff[i]
          if(temp>15){
            temp=idx;
            break;
          }
          this.rs.push(temp);
          if(i===len-1){
            i=0
          }
        }
        for(let i=len-1;i>-1;i--){
                  
          temp-=this.normalNoteDiff[i]
          if(temp<-1){
            break;
          }  
          this.rs.unshift(temp);
          if(i=-1){
            i=len-1;
          }
        }
        console.log("音阶：",this.rs);
        console.log(idx,this.segNotes);
        this.$set(this.segNotes,idx,{
          sup:this.segNotes[idx].sup,
          note:this.segNotes[idx].note,
          ncode:this.segNotes[idx].ncode,
          show:true
        })
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
            this.segNotes.push(
              {
                note:String.fromCharCode(segNoteCode),
                ncode:segNoteCode,
                sup:''
              }
            )
            
          }else{
            this.segNotes.push(
              {
                note:String.fromCharCode(segNoteCode),
                ncode:segNoteCode,
                sup:''
              }
            )
            this.segNotes.push(
              {
                note:String.fromCharCode(segNoteCode),
                ncode:segNoteCode,
                sup:'#'
              }
            )
            
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