<template lang="pug">
  v-container()
    h2 プロフィール
    v-content
      v-card
        v-container(fluid)
          v-content
            div
              div.headline Name
              p ktr03282
        v-container(fluid)
          v-content
            div
              div.headline 詳細
              p 専門学校 3回生
        v-container(fluid)
          v-content
            div.headline だいたいこんな人
            v-layout(row wrap)
              v-flex(md6)
                RadarChart(:data="radar.charactar" :options="radar.options" style="max-width: 300px")
              v-flex(md6)
                RadarChart(:data="radar.skill" :options="radar.options" style="max-width: 300px")
        v-container(fluid)
          v-content
            div.headline 言語習得度
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
              data: [6, 3, 3, 2, 4]
            }
          ]
        },
        language: {
          labels: [
            "Javascript", "Node.js", "HTML/CSS", "Java",
            "PHP", "Ruby", "Python", "Kotlin (Not Android)", "Swift", "C#"
          ],
          datasets: [
            {
              backgroundColor: colors.green,
              borderColor: colors.green,
              data: [7, 7, 5, 6, 4, 3, 3, 4, 2, 2]
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

<style>
</style>
