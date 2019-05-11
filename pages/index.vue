<template>
  <v-jumbotron>
    <v-container fill-height>
      <v-layout align-center>
        <v-flex>
          <h3 class="display-3">
            ドキュメントの個人識別情報をマスキング
          </h3>

          <div class="subheading">
            組織が扱う大量のドキュメントやデータには個人を特定できる情報が含まれます。
          </div>
          <div class="subheading">
            そのため、目視で個人情報の漏洩可能性のあるデータのチェック、特定、対処は時間とコスト大幅にかかります。
          </div>
          <div class="subheading">
            組織に損害を与えるような情報漏えいを防ぐために、個人を特定できる情報を伏せ字にし、この情報を安全に保管・共有できるようにします。
          </div>

          <v-divider class="my-3" />
          <!-- <div>
            <v-icon large color="blue darken-2">chat</v-icon>
            <div class="title mb-3">
              形態素解析はAI(人工知能)の自然言語処理の過程でも使用されています。
              コンピューターであるAIに、あいまいな表現などが多い自然言語を、プログラムを組んで処理してもらう場合、「自然言語処理」という特別な処理が必要になります。
              日本語での自然言語処理を行う場合、処理してほしい文章を「形態素解析」「構文解析」「意味解析」「文脈解析」というようにさまざまな解析を行い、やっとコンピューターが自然言語の意味を処理できるようになるのです。
              日本語での自然言語処理をする時、単語を最小単位にまで分割できる形態素解析の機能はとても重要です。
            </div>
          </div> -->

          <div class="title mb-3">
            Check out our newest features!
          </div>

          <v-btn
            class="mx-0"
            color="primary"
            large
            to="/masking"
          >
            デモページ
          </v-btn>
        </v-flex>
      </v-layout>
    </v-container>
  </v-jumbotron>
</template>

<script>
export default {}
</script>
