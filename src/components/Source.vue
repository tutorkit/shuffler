<template>
  <div>
	  <h2 class="title">Source</h2>
    <div>
			<div class="field">
        <label class="label">skip first</label>
        <div class="control">
          <label class="radio"><input type="radio" v-model="skip_first" value="1" /> Yes</label>
          <label class="radio"><input type="radio" v-model="skip_first" value="0" /> No</label>
        </div>
			</div>
			
      <div class="field">
        <label class="label">skip last</label>
        <div class="control">
          <label class="radio"><input type="radio" v-model="skip_last" value="1" /> Yes</label>
          <label class="radio"><input type="radio" v-model="skip_last" value="0" /> No</label>
        </div>
			</div>

    </div>

    <div>
      <textarea class="textarea" v-model="source" rows="10"></textarea>
    </div>

    <div class="contents_viewer">
      <ul v-if="lines.length">
        <ContentsItem v-for="item in lines" :key="item.no" :item="item" />
      </ul>
    </div>
  </div>
</template>

<script>
import ContentsItem from './ContentsItem.vue'

var sample_source = "Whales are a widely distributed and diverse group of fully aquatic placental marine mammals.\n\
They are an informal grouping within the infraorder Cetacea, usually excluding dolphins and porpoises.\n\
Whales, dolphins and porpoises belong to the order Cetartiodactyla with even-toed ungulates and their closest living relatives are the hippopotamuses, having diverged about 40 million years ago.\n\
The two parvorders of whales, baleen whales (Mysticeti) and toothed whales (Odontoceti), are thought to have split apart around 34 million years ago.\n\
The whales comprise eight extant families: Balaenopteridae (the rorquals), Balaenidae (right whales), Cetotheriidae (the pygmy right whale), Eschrichtiidae (the grey whale), Monodontidae (belugas and narwhals), Physeteridae (the sperm whale), Kogiidae (the dwarf and pygmy sperm whale), and Ziphiidae (the beaked whales).";

var sample_contents = [
  {no: 0, skipped: true, text: "Whales are a widely distributed and diverse group of fully aquatic placental marine mammals." },
  {no: 1, text: "They are an informal grouping within the infraorder Cetacea, usually excluding dolphins and porpoises." },
  {no: 2, text: "Whales, dolphins and porpoises belong to the order Cetartiodactyla with even-toed ungulates and their closest living relatives are the hippopotamuses, having diverged about 40 million years ago." },
  {no: 3, text: "The two parvorders of whales, baleen whales (Mysticeti) and toothed whales (Odontoceti), are thought to have split apart around 34 million years ago." },
  {no: 4, skipped: true, text: "The whales comprise eight extant families: Balaenopteridae (the rorquals), Balaenidae (right whales), Cetotheriidae (the pygmy right whale), Eschrichtiidae (the grey whale), Monodontidae (belugas and narwhals), Physeteridae (the sperm whale), Kogiidae (the dwarf and pygmy sperm whale), and Ziphiidae (the beaked whales)." }
];
sample_contents = [];

export default {
  components: {
    ContentsItem,
  },
  computed: {
    lines: function() {
      var lines = this.source.split('\n');
      var buf = [];
      for (var x in lines) {
        var line = lines[x];
        if (line == "") {
          continue;
        }
        buf.push({ no: x, text: lines[x], skipped: false });
      }
      if (this.skip_first > 0 && buf.length > 0) {
        buf[0].skipped = true
      }
      if (this.skip_last > 0 && buf.length > 2) {
        buf[buf.length-1].skipped = true
      }
      console.log("buf", buf)
      return buf;
      //return sample_contents;
    }
  },
  data () {
    return {
      skip_first: 0,
      skip_last: 0,
      source: sample_source
    }
  }
}
</script>

<style scoped>
.contents_viewer {
  margin: 2em 0;
}
</style>