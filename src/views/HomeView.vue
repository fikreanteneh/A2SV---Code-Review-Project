<template>
  <HeaderTitle :title="titleString"></HeaderTitle>
  <p class="text-center my-4 text-xl mx-16"
    >This is a program that tries to depict the DDA line drawing algorithm.
    Enter your intial and final co-ordiante value of the line and it will create
    the corresponding image in pixel.</p
  >
  <InputFields></InputFields>
</template>

<script>
import HeaderTitle from "../components/HeaderTitle.vue";
import ParagraphComp from "../components/ParagraphComp.vue";
import InputFields from "../components/InputFields.vue";

export default {
  data() {
    return {
      titleString: "Digital Differential Analyzer (DDA) Line Drawing Algorithm",
    };
  },
  props: ["title"],
  components: {
    HeaderTitle,
    ParagraphComp,
    InputFields,
  },
};
</script>
