<template>
  <div class="profile-box">

<!--    <img :src="user.avatarUrl" alt="头像" class="avatar" />-->
<!--    <h2>{{ user.name }}</h2>-->
<!--    <h2>{{ user.en_name }}</h2>-->
<!--    <h4>{{ user.email }}</h4>-->
    <div class="profile-header">
      <img :src="user.avatarUrl" alt="avatar" class="avatar-square" />
      <div class="info">
        <h1>{{ user.name }}</h1>
        <p>邮箱：{{ user.email }}</p>
        <p>电话：{{ user.phone }}</p>
        <p>微信：{{user.wechat}}</p>
      </div>
    </div>
    <hr />
    <h3 class="section-title" >Publication</h3>
    <ul>
    <li v-for="(paper, index) in user.papers" :key="index">
      <p v-html="formatPaper(paper)"></p>
    </li>
    </ul>
    <hr />
    <h3 class="section-title" >About Me</h3>
    <p>{{ user.bio }}</p>
  </div>
</template>

<script>
export default {
  name: 'ProfileCard',
  methods: {
    formatPaper(paper) {
      return `${paper.title} <a href="${paper.link}" target="_blank">${paper.link}</a>`;
    }
  },
  data() {
    return {
      user: {
        name: "李志强",
        en_name:"Klay Li",
        email: "zql\_up@163.com",
        bio: "I obtained my bachelor's degree in Software Engineering from Shandong University of Technology, and my master's degree in Software Engineering from China University of Petroleum (East China), where I focused on network resource allocation. In my personal life, I enjoy running, hiking, and reading biographies and books on psychology.",
        avatarUrl: "src/pic/tx.jpg",
        phone:'18264728763',
        wechat:'zql_up77',
        papers:[
          {
            title: "P. Zhang, <strong>Z. Li</strong>, M. Guizani, N. Kumar, K. Yu and J. Wang, Energy Aware Space-Air-Ground Integrated Network Resource Orchestration Algorithm, <em>IEEE Transactions on Vehicular Technology</em>.",
            link: "https://ieeexplore.ieee.org/document/10631705",
          }
        ]
      }
    };
  }
};
</script>

<style scoped>
.profile-box {
  background: #fff;
  padding: 24px;
  border-radius: 12px;
  max-width: 600px;
  margin: 40px auto;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  text-align: center;
}
.profile-header {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 16px;
}
.avatar-square {
  width: 200px;
  height: 200px;
  border-radius: 8px;
  object-fit: cover;
}
.info h1 {
  margin: 0 130px 10px;
}
.info p {
  margin: 4px 70px;
  font-size: 20px;
  color: #555;
}
h2, h4 {
  margin: 8px 0;
}
p {
  color: #100f0f;
  line-height: 1.6;
  white-space: pre-wrap;
  text-align: left;
}
.section-title{
  text-align: left;
}
</style>
