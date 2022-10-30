<template>
  <v-list-group
    v-for="niveluno in menusList"
    :key="niveluno.nombre"
    no-action
    class="p-0"
  >
    <template v-slot:activator>
      <pt-menu-item
        :icon="niveluno.icon"
        :title="niveluno.nombre"
      ></pt-menu-item>
    </template>

    <v-list-item v-for="niveldos in niveluno.children" :key="niveldos.nombre">
      <pt-menu-item
        :icon="niveldos.icon"
        :title="niveldos.nombre"
      ></pt-menu-item>

      <v-list-item
        v-for="nivelTres in niveldos.children"
        :key="nivelTres.nombre"
        class="pl-8"
      >
        <pt-menu-item
          :icon="nivelTres.icon"
          :title="nivelTres.nombre"
        ></pt-menu-item>
      </v-list-item>
    </v-list-item>
  </v-list-group>
</template>

<template>
  <v-list>
    <v-list-group v-for="node in nodes" v-model="node.active">
      <v-list-tile slot="activator" @click="">
        <v-list-tile-title>{{ node.text }}</v-list-tile-title>
      </v-list-tile>
      <v-list class="py-0 pl-1">
        <v-list-group v-for="child in node.children" v-model="child.active">
          <v-list-tile slot="activator" @click="">
            <v-list-tile-title>{{ child.text }}</v-list-tile-title>
          </v-list-tile>
          <v-list class="py-0 pl-2" v-for="grandchild in child.children">
            <v-list-tile>
              <v-list-tile-title>{{ grandchild.text }}</v-list-tile-title>
            </v-list-tile>
          </v-list>
        </v-list-group>
      </v-list>
    </v-list-group>
  </v-list>
</template>
