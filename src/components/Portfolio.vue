<template>
  <div class="container-portfolio">
    <header>
      <img class="titre-byfabe" src="../assets/byfabe.png" alt="titre byfabe" />
      <img class="logo-cyber" src="../assets/cyber.png" alt="Logo cyber" />
    </header>
    <div class="line"></div>
    <div class="container-bio">
      <div class="photo">
        <img class="photo-profile" src="../assets/profile.png" alt="" />
      </div>
      <div class="bio">
        <p><span class="color-bio">Prénom:</span> Fabien</p>
        <p><span class="color-bio">Âge:</span> 35 ans</p>
        <p><span class="color-bio">Localisation:</span> France</p>
        <p><span class="color-bio">Classe:</span> Développeur web junior</p>
        <p><span class="color-bio">Caratère:</span> Ça va :)</p>
        <p><span class="color-bio">Bio:</span> Mon imagination pour seule limite ! </p>
      </div>
    </div>
    <div class="line"></div>
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
  & .titre-byfabe {
    width: clamp(250px, 50vw, 1500px);
    margin-top: 6%;
  }
  & .logo-cyber {
    width: 15vw;
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
    opacity: 0.2;
  }
  20%,
  21.999%,
  63%,
  63.999%,
  65%,
  69.999% {
    opacity: 0.1;
  }
}
.line {
  width: 20vw;
  height: 4px;
  box-shadow: 0 0 20px rgba(255, 39, 183, 0.712),
    inset 0 0 10px rgba(250, 63, 178, 0.726), 0 2px 0 #000;
  margin: 5% 0 5% 0;
}
.container-bio {
  display: flex;
  justify-content: space-around;
  width: 100%;
  & .photo-profile {
    width: clamp(20px, 20vw, 500px);
    height: auto;
  }
  & .bio {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    width: 50vw;
    & p {
      font-size: 1.5vw;
      font-family: "Press Start 2P", cursive;
      color: #f1f1f1;
      padding: 20px;
    }
  }
  & .color-bio {
    color: aqua;
  }
}
</style>
