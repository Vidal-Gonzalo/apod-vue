<template>
  <div class="footer" id="footer">
    <span class="ms-3">Gonzalo Vidal | 2021</span>
    <ul class="me-3">
      <li>
        <a href="https://www.github.com/Vidal-Gonzalo" target="_onblank"
          ><i class="bi-github" role="img" aria-label="github"></i
        ></a>
      </li>
      <li>
          <a href="https://www.linkedin.com/in/vidal-gonzalo/" target="_onblank"><i class="bi-linkedin" role="img" aria-label="linkedin"></i></a></li>
    </ul>
  </div>
</template>

<style scoped>
.footer {
  font-family: "Barlow Condensed", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  width: 100%;
  color: #fff;
  background-color: rgba(26, 2, 30, 1.0);
}
.footer ul {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.footer ul li {
  list-style: none;
  margin: 15px 10px 0px 10px;
}
a {
  color: #fff;
}
</style>