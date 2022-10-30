<template>
  <header>
    <div class="contenedor">
      <h2 class="logotipo">comics</h2>
      <nav>
        <a href="#" class="activo">Inicio</a>
        <a href="#">comics</a>
        <a href="#">Characters</a>
        <a href="#">Comics Recientes</a>
        <router-link to="/tags">Tags</router-link>

        <select
          class="form-select me-2 selecTipoBusqueda"
          aria-label="Default select example"
          id="selectTipo"
        >
          <option value="comics">comics</option>
          <option value="characters">characters</option>
        </select>
        <input
          id="buscar"
          class="form-control me-2"
          type="search"
          placeholder="Buscar"
          aria-label="Buscar"
        />
        <button class="btn btn-outline-danger" id="btnSearch">Search</button>
      </nav>
    </div>
  </header>
</template>

<style>
header {
  padding: 30px 0;
}

header .contenedor {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header .logotipo {
  font-family: "Bebas Neue", cursive;
  font-weight: normal;
  color: var(--rojo);
  font-size: 40px;
}

header nav a {
  color: #aaa;
  text-decoration: none;
  margin-right: 20px;
}

header nav a:hover,
header nav a.activo {
  color: #fff;
}
</style>
