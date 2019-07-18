<template>
  <div id="app">
    <router-view/>
  </div>
</template>
<style>
  body {
    margin: 0;
    padding: 0;
    font-family: 'Roboto', sans-serif;
    font-size: 16px;
  }
  p {
    padding: 0;
    margin: 0;
  }
  .card-actions {
    width: 100%;
  }
  .btn {
    width: 100%;
    background-color: #fff;
    border: 1px solid rgba(0, 0, 0, 0.27);
    border-radius: 5px;
    padding: 10px;
    color: rgba(0, 0, 0, 0.27);
  }
  .home {
    min-height: 100vh;
    width: 100%;
    background-color: gray;
  }
  .__wrapper-main-insert-block {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-around;
    flex-flow: row wrap;
  }
  .card {
    width: 24%;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-flow: row wrap;
    border-radius: 10px;
    background-color: #fff;
    margin: 5px;
  }
  .card .card-body {
    text-align: center;
    padding: 0;
    width: 100%;
  }
  .card .card-actions {
    padding: 10px;
    margin-top: -25px;
  }
  .table-results {
    width: 100%;
    min-height: 100px;
    cursor: pointer;
    height: 300px;
  }
  .img {
    width: 100%;
    position: relative;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .img img{

  }
  ul {
    padding: 0;
    margin: 0;
  }
  ul li {
    list-style-type: none;
    padding: 15px;
  }
  .date-text {
    color: green;
    font-weight: 600;
  }
  .__li-insert-text {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 5px;
    margin-bottom: 5px;
  }
  ._block-insert-2 {
    padding-right: 20px;
    padding-left: 20px;
  }
  .description {
    color: gray;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    font-size: 0.8rem;
  }
  .text-uppercase {
    text-transform: uppercase;
    font-size: .9rem;
  }
  .t-blue {
    color: blue;
  }
  .bold-text {
    font-weight: 700;
  }
  table {
    width: 100%;
    padding: 10px;
    border-spacing: 0;
  }
  table thead {
    background-color:rgba(128, 128, 128, 0.06);
    padding: 15px;
  }
  table tbody  {
    overflow: scroll;
    height: 100px;
  }
  .border_bottom td {
    border-bottom: 1px solid rgba(128, 128, 128, 0.16);
    height: 30px;
  }
  table tbody tr td {
    font-size: .8rem;
    padding: 5px;
    font-weight: 400;
  }
  table thead tr th {
    border-spacing: 0;
    padding: 0;
    margin: 0;
    padding: 10px;
    font-size: 0.7rem;
    border-bottom: 1px solid #ddd;
  }
  .wraper-card-components {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-around;
    flex-flow: row wrap;
  }
  .image-bg {
    position: relative;
    width: 100%;
    height: 300px;
    border-radius: 10px 10px 0 0
  }
  .img-main-bg {
    position: absolute;
    z-index: 1;
    top: 0;
  }
</style>


