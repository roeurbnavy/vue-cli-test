<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <div class="header">
      <slot name="header" />
    </div>

    <div class="topnav">
      <slot name="topnav" />
    </div>

    <slot></slot>
  </div>
</template>

<script setup></script>

<style>
/* Style the header */
.header {
  background-color: #f1f1f1;
  padding: 20px;
  text-align: center;
}

/* Style the top navigation bar */
.topnav {
  overflow: hidden;
  background-color: #333;
}

/* Style the topnav links */
.topnav a {
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

/* Change color on hover */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}
</style>
