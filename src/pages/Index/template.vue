<template>
  <div id="index">
    <section class="blog-posts">
      <router-link class="item" v-for="blog in blogs" :key="blog.id" :to="`/detail/${blog.id}`">
        <figure class="avatar">
          <router-link :to="{path:`/user/${blog.user.id}`}">
            <img :src="blog.user.avatar" :alt="blog.user.username">
          </router-link>

          <figcaption><router-link :to="{path:`/user/${blog.user.id}`}">
            {{blog.user.username}}
          </router-link></figcaption>
        </figure>
        <h3>{{blog.title}}<span> 发布于{{friendlyDate(blog.createdAt)}}</span></h3>
        <p>{{blog.description}}</p>
      </router-link>
    </section>
    <section class="pagination">
      <el-pagination
        layout="prev, pager, next"
        @current-change = "onPageChange"
        :total="total">
      </el-pagination>
    </section>
  </div>
</template>

<script src="./template.js"></script>

<style scoped lang="less" src="./template.less"></style>
