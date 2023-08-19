<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <div class="form-floating">
          <select
            v-model="selectedDate"
            class="form-select form-select-lg"
            aria-label="Seleccione un día"
            id="dateSelect"
          >
            <option v-for="date in activeDates" :value="date[0]" :key="date[0]">
              {{ date[1].label }}
            </option>
          </select>
          <label for="dateSelect" class="form-label">Fecha</label>
        </div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-12">
        <div class="form-floating">
          <select
            v-model="selectedGroup"
            class="form-select form-select-lg"
            aria-label="Seleccione un grupo"
            id="groupSelect"
          >
            <option value="">Todos</option>
            <option
              v-for="(group, index) in groups"
              :value="index"
              :key="index"
            >
              {{ group }}
            </option>
          </select>
          <label for="groupSelect" class="form-label">Grupo</label>
        </div>
      </div>
    </div>
    <div
      v-if="selectedDate !== '' && selectedGroup === ''"
      class="row justify-content-center mt-4 mb-4"
    >
      <div
        v-for="(group, index) in dates[selectedDate]"
        :key="index"
        class="col-auto"
      >
        <div class="card mt-3" style="width: 18rem">
          <div class="card-header text-center">
            <h6>{{ groups[index] }}</h6>
          </div>
          <div class="card-body">
            <div class="col-12">
              Dejar en
              <strong
                ><i>{{ group.drop_off_at }}</i></strong
              >
            </div>
            <div class="col-12">
              Recoger en
              <strong
                ><i>{{ group.pick_up_at }}</i></strong
              >
            </div>
          </div>
        </div>
      </div>
    </div>

    <div
      v-if="selectedDate !== '' && selectedGroup !== ''"
      class="row justify-content-center mt-4"
    >
      <div class="col-auto">
        <div class="card mt-3" style="width: 18rem">
          <div class="card-header text-center">
            <h6>{{ groups[selectedGroup] }}</h6>
          </div>
          <div class="card-body">
            <div class="col-12">
              Dejar en
              <strong
                ><i>{{
                  dates[selectedDate][selectedGroup].drop_off_at
                }}</i></strong
              >
            </div>
            <div class="col-12">
              Recoger en
              <strong
                ><i>{{
                  dates[selectedDate][selectedGroup].pick_up_at
                }}</i></strong
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      dates: {
        "05_08_2023": {
          saltamontes: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          colibries: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          enlazadores: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          exploradores_creativos: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          sueno_de_lobos: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
        },
        "12_08_2023": {
          saltamontes: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          colibries: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          enlazadores: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          exploradores_creativos: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          sueno_de_lobos: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
        },
        "19_08_2023": {
          saltamontes: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          colibries: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          enlazadores: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          exploradores_creativos: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          sueno_de_lobos: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
        },
        "26_08_2023": {
          saltamontes: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          colibries: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          enlazadores: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          exploradores_creativos: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          sueno_de_lobos: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
        },
        "02_09_2023": {
          saltamontes: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          colibries: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          enlazadores: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          exploradores_creativos: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          sueno_de_lobos: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
        },
        "09_09_2023": {
          saltamontes: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          colibries: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          enlazadores: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          exploradores_creativos: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          sueno_de_lobos: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
        },

        "16_09_2023": {
          saltamontes: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          colibries: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          enlazadores: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          exploradores_creativos: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          sueno_de_lobos: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
        },
        "23_09_2023": {
          saltamontes: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          colibries: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          enlazadores: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          exploradores_creativos: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          sueno_de_lobos: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
        },
        "30_09_2023": {
          saltamontes: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          colibries: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          enlazadores: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          exploradores_creativos: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          sueno_de_lobos: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
        },
        "07_10_2023": {
          saltamontes: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          colibries: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          enlazadores: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          exploradores_creativos: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          sueno_de_lobos: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
        },
        "14_10_2023": {
          saltamontes: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          colibries: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          enlazadores: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          exploradores_creativos: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          sueno_de_lobos: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
        },
        "21_10_2023": {
          saltamontes: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          colibries: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          enlazadores: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          exploradores_creativos: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          sueno_de_lobos: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
        },
        "28_10_2023": {
          saltamontes: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          colibries: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          enlazadores: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          exploradores_creativos: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          sueno_de_lobos: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
        },
        "04_11_2023": {
          saltamontes: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          colibries: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          enlazadores: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
          exploradores_creativos: {
            drop_off_at: "Cerámica",
            pick_up_at: "Yoga",
          },
          sueno_de_lobos: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
        },
        "11_11_2023": {
          saltamontes: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          colibries: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          enlazadores: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
          exploradores_creativos: {
            drop_off_at: "Baile",
            pick_up_at: "Pintura",
          },
          sueno_de_lobos: {
            drop_off_at: "Yoga",
            pick_up_at: "Cerámica",
          },
        },
        "17_11_2023": {
          saltamontes: {
            drop_off_at: "Teatro",
            pick_up_at: "Agroecología",
          },
          colibries: {
            drop_off_at: "Agroecología",
            pick_up_at: "Teatro",
          },
          enlazadores: {
            drop_off_at: "Fomento",
            pick_up_at: "Música",
          },
          exploradores_creativos: {
            drop_off_at: "Música",
            pick_up_at: "Fomento",
          },
          sueno_de_lobos: {
            drop_off_at: "Pintura",
            pick_up_at: "Baile",
          },
        },
      },
      selectedDate: "",
      selectedGroup: "",
      groups: {
        saltamontes: "Saltamontes",
        colibries: "Colibries",
        enlazadores: "Enlazadores",
        exploradores_creativos: "Exploradores reativos",
        sueno_de_lobos: "Sueño de lobos",
      },
      datesLabels: {
        "05_08_2023": {
          label: "Agosto 5",
          date: new Date(2023, 8 - 1, 5, 23, 59, 59),
        },
        "12_08_2023": {
          label: "Agosto 12",
          date: new Date(2023, 8 - 1, 12, 23, 59, 59),
        },
        "19_08_2023": {
          label: "Agosto 19",
          date: new Date(2023, 8 - 1, 19, 23, 59, 59),
        },
        "26_08_2023": {
          label: "Agosto 26",
          date: new Date(2023, 8 - 1, 26, 23, 59, 59),
        },
        "02_09_2023": {
          label: "Septiembre 2",
          date: new Date(2023, 9 - 1, 2, 23, 59, 59),
        },
        "09_09_2023": {
          label: "Septiembre 9",
          date: new Date(2023, 9 - 1, 9, 23, 59, 59),
        },
        "16_09_2023": {
          label: "Septiembre 16",
          date: new Date(2023, 9 - 1, 16, 23, 59, 59),
        },
        "23_09_2023": {
          label: "Septiembre 23",
          date: new Date(2023, 9 - 1, 23, 23, 59, 59),
        },
        "30_09_2023": {
          label: "Septiembre 30",
          date: new Date(2023, 9 - 1, 30, 23, 59, 59),
        },
        "07_10_2023": {
          label: "Octubre 7",
          date: new Date(2023, 10 - 1, 7, 23, 59, 59),
        },
        "14_10_2023": {
          label: "Octubre 14",
          date: new Date(2023, 10 - 1, 14, 23, 59, 59),
        },
        "21_10_2023": {
          label: "Octubre 21",
          date: new Date(2023, 10 - 1, 21, 23, 59, 59),
        },
        "28_10_2023": {
          label: "Octubre 28",
          date: new Date(2023, 10 - 1, 28, 23, 59, 59),
        },
        "04_11_2023": {
          label: "Noviembre 4",
          date: new Date(2023, 11 - 1, 4, 23, 59, 59),
        },
        "11_11_2023": {
          label: "Noviembre 11",
          date: new Date(2023, 11 - 1, 11, 23, 59, 59),
        },
        "17_11_2023": {
          label: "Noviembre 17",
          date: new Date(2023, 11 - 1, 17, 23, 59, 59),
        },
      },
    };
  },
  computed: {
    activeDates() {
      return Object.entries(this.datesLabels).filter(
        (d) => d[1].date >= new Date()
      );
    },
    firstDate() {
      return this.activeDates[0][0];
    },
  },
  mounted() {
    this.selectedDate = this.firstDate;
  },
};
</script>

<style></style>
