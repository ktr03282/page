<template lang="pug">
  v-container()
    v-content
      v-card(flat)
        v-toolbar(color="secondary" flat)
          v-toolbar-title
            v-icon(color="primary" medium) account_circle
            span プロフィール
        v-container(fluid)
          v-content
            div.headline Who?
            v-layout(row wrap)
              v-flex(md6)
                img(src="/profile.jpg" style="width: 70%")
              v-flex(md6)
                p(v-for="(text, index) in profile.detail.texts" :key="index") {{text}}
                div.social-icons
                  div
                    a(href="https://github.com/ktr0328")
                      v-btn(round color="primary")
                        v-icon fab fa-github
                        span 開発用
                  div
                    a(href="https://github.com/ktr03282")
                      v-btn(round color="primary")
                        v-icon fab fa-github
                        span 公開用
                  div
                    a(href="https://scrapbox.io/ktr0328/")
                      v-btn(round color="primary")
                        v-icon fas fa-sticky-note
                        span Scrapbox
        v-container(fluid)
          v-content
            div.headline Ability
            v-layout(row wrap)
              v-flex(md6)
                RadarChart(:data="radar.charactar" :options="radar.options" style="max-width: 280px")
              v-flex(md6)
                RadarChart(:data="radar.skill" :options="radar.options" style="max-width: 280px")
        v-container(fluid)
          v-content
            div.headline Language
            RadarChart(:data="radar.language" :options="radar.options" style="max-width: 400px")
</template>

<script>
import RadarChart from "~/components/RadarChart"
import BarChart from "~/components/BarChart"

const colors = {
  blue: "rgba(54, 162, 235, 0.5)",
  yellow: "rgba(235, 162, 54, 0.5)",
  green: "rgba(54, 200, 54, 0.5)"
}

export default {
  name: "profile",
  data() {
    return {
      profile: {
        name: "ktr0328",
        detail: {
          texts: [
            "名前: ktr0328",
            "1992/3/28生まれ。",
            "京都在住・専門学校3回生。",
            "兵庫県神戸市育ち。",
            "コーヒーが好き。",
            "プログラミング3年目のぺーぺー。",
            "フロントエンドのコーディングが強みだが、別段好きでもないという矛盾を抱えている。",
            "学習のモチベーションは全て好奇心。",
            "やりたいことが多すぎて、時間が圧倒的に足りないのが悩み。",
            "現在、HaskellやDocker、AWSを学習中。"
          ]
        },
        Supplement: {}
      },
      radar: {
        charactar: {
          labels: [
            "要領の良さ",
            "コミュニケーション力",
            "プレゼン力",
            "好奇心",
            "集中力",
            "問題解決力"
          ],
          datasets: [
            {
              borderColor: colors.blue,
              backgroundColor: colors.blue,
              data: [4, 5, 3, 8, 8, 5]
            }
          ]
        },
        skill: {
          labels: [
            "フロントエンド",
            "ネットワーク",
            "データベース",
            "セキュリティ",
            "サーバー"
          ],
          datasets: [
            {
              borderColor: colors.yellow,
              backgroundColor: colors.yellow,
              data: [7, 4, 4, 3, 5]
            }
          ]
        },
        language: {
          labels: [
            "Javascript", "Node.js", "HTML/CSS", "Java",
            "PHP", "Ruby", "Python", "Kotlin", "Swift", "C#"
          ],
          datasets: [
            {
              backgroundColor: colors.green,
              borderColor: colors.green,
              data: [8, 8, 5, 6, 4, 3, 3, 4, 2, 2]
            }
          ]
        },
        options: {
          showTooltips: false,
          legend: false,
          scale: {
            display: true,
            ticks: {
              beginAtZero: true,
              display: false,
              min: 0,
              max: 10
            }
          }
        }
      }
    };
  },
  components: {
    RadarChart,
    BarChart
  }
};
</script>

<style scoped lang="sass">
.headline
  border-bottom: 1px solid rgba(150, 150, 150, 0.3)
  margin-bottom: 5px
.social-icons
  text-align: right
  span
    padding-left: 5px
</style>
