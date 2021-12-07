<template>
  <div class="container-portfolio">
    <header>
      <img class="nebuleuse" src="../assets/nebuleuse.png" alt="" />
      <img class="titre-byfabe" src="../assets/byfabe.png" alt="titre byfabe" />
      <img class="logo-cyber" src="../assets/cyber.png" alt="Logo cyber" />
    </header>
    <div class="line"></div>
    <div class="container-bio">
      <div class="photo">
        <img class="photo-profile" src="../assets/profile.png" alt="" />
      </div>
      <div class="bio">
        <h2>Bio</h2>
        <p><span class="color-bio">Prénom:</span> Fabien</p>
        <p><span class="color-bio">Âge:</span> 35 ans</p>
        <p><span class="color-bio">Localisation:</span> France</p>
        <p><span class="color-bio">Classe:</span> Développeur web junior</p>
        <p><span class="color-bio">Caratère:</span> Ça va :)</p>
        <div class="p-bio">
          <p>
            <span class="color-bio">Bio:</span>
          </p>
          <p>Mon imagination pour seule limite !</p>
        </div>
      </div>
    </div>
    <div class="line"></div>
    <div class="container-project">
      <div class="list-project">
        <h2>Projets</h2>
        <a href="https://www.memento.cool"
          ><img src="../assets/mem.jpg" alt=""
        /></a>
        <a href="https://objective-poincare-859034.netlify.app/#/"
          ><img src="../assets/honf.jpg" alt=""
        /></a>
      </div>
    </div>
    <div class="line"></div>
    <div class="container-skills">
      <h2>Skills</h2>
      <img src="../assets/html_css_js.png" alt="" />
      <img src="../assets/vue.png" alt="" />
      <img src="../assets/node.png" alt="" />
      <img src="../assets/express.png" alt="" />
      <img src="../assets/mongodb.png" alt="" />
      <img src="../assets/ps.png" alt="" />
    </div>
  </div>
</template>

<script>
export default {};
</script>


<style scoped lang="scss">
.container-portfolio {
  display: flex;
  flex-direction: column;
  align-items: center;
}
header {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  & .nebuleuse {
    position: absolute;
    top: 0;
    z-index: -5;
  }
  & .titre-byfabe {
    width: clamp(250px, 40vw, 1500px);
    margin-top: 6%;
  }
  & .logo-cyber {
    width: 12vw;
    height: auto;
    animation: blink 3s cubic-bezier(0.1, -0.6, 0.2, 0) infinite;
  }
}
@keyframes blink {
  0%,
  19.999%,
  22%,
  62.999%,
  64%,
  64.999%,
  70%,
  100% {
    opacity: 0.6;
  }
  20%,
  21.999%,
  63%,
  63.999%,
  65%,
  69.999% {
    opacity: 0.4;
  }
}
.line {
  width: 30vw;
  height: 4px;
  box-shadow: 0 0 20px rgba(255, 39, 183, 0.712),
    inset 0 0 10px rgba(250, 63, 178, 0.726), 0 2px 0 #000;
  margin: 5% 0 5% 0;
}
.container-bio {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100%;
  & .photo-profile {
    width: clamp(20px, 17vw, 500px);
    height: auto;
  }
  & .bio {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    width: 50vw;
    & p {
      font-size: 1vw;
      font-family: "Press Start 2P", cursive;
      color: #f1f1f1;
      padding: 20px;
      white-space: break-spaces;
    }
  }
  & .color-bio {
    color: aqua;
  }
  & .p-bio {
    display: flex;
  }
}
h2 {
  font-size: 2.8vw;
  color: #f1f1f1;
  font-family: "Press Start 2P", cursive;
  margin-bottom: 8%;
  text-align: center;
}
.container-project {
  & .list-project {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  & a {
    width: 40vw;
    & :hover {
      box-shadow: 0 0 22px rgba(39, 223, 255, 0.712),
      inset 0 0 10px rgba(63, 228, 250, 0.5), 0 2px 0 #000;
      transition: all 0.3s ease-in-out;
    }
  }
  & img {
    width: 100%;
    box-sizing: content-box;
    border-radius: 5px;
    border: 2px solid rgb(32, 145, 238);
    box-shadow: 0 0 12px rgba(39, 223, 255, 0.712),
      inset 0 0 10px rgba(63, 228, 250, 0.5), 0 2px 0 #000;
    margin-bottom: 7%;
    transition: all 0.3s ease-in-out;
  }
}
.container-skills {
  display: flex;
  flex-direction: column;
  align-items: center;
  & :nth-child(2) {
    margin: 15% 0 15% 0;
  }
  & :nth-child(7) {
    width: 10vw;
  }
}
.container-skills img {
  width: 15vw;
}
</style>
