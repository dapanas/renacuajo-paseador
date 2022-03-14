<template>
  <div class="container">
    <div class="row">
      <div class="col-6">
        <div class="form-floating">
          <select v-model="selectedDate" class="form-select form-select-lg" aria-label="Seleccione un día"
                  id="dateSelect">
            <option v-for="date in activeDates" :value="date[0]" :key="date[0]">
              {{ date[1].label }}
            </option>
          </select>
          <label for="dateSelect" class="form-label">Fecha</label>
        </div>
      </div>
      <div class="col-6">
        <div class="form-floating">
          <select v-model="selectedGroup" class="form-select form-select-lg" aria-label="Seleccione un grupo"
                  id="groupSelect">
            <option value="">Todos</option>
            <option v-for="(group, index) in groups" :value="index" :key="index">
              {{ group }}
            </option>
          </select>
          <label for="groupSelect" class="form-label">Grupo</label>
        </div>
      </div>
    </div>
    <div v-if="selectedDate !== '' && selectedGroup === ''" class="row justify-content-center mt-4 mb-4">
      <div v-for="(group, index) in dates[selectedDate]" :key="index" class="col-auto">
        <div class="card mt-3" style="width: 18rem;">
          <div class="card-header text-center">
            <h6>{{ groups[index] }}</h6>
          </div>
          <div class="card-body">
            <div class="col-12">Dejar en <strong><i>{{ group.drop_off_at }}</i></strong></div>
            <div class="col-12">Recoger en <strong><i>{{ group.pick_up_at }}</i></strong></div>
          </div>
        </div>
      </div>
    </div>

    <div v-if="selectedDate !== '' && selectedGroup !== ''" class="row justify-content-center mt-4">
      <div class="col-auto">
        <div class="card mt-3" style="width: 18rem;">
          <div class="card-header text-center">
            <h6>{{ groups[selectedGroup] }}</h6>
          </div>
          <div class="card-body">
            <div class="col-12">Dejar en <strong><i>{{ dates[selectedDate][selectedGroup].drop_off_at }}</i></strong></div>
            <div class="col-12">Recoger en <strong><i>{{ dates[selectedDate][selectedGroup].pick_up_at }}</i></strong></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      dates: {
        "19_02_2022": {
          "gotitas": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "cantores": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "alfareros": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "azulejos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sembradores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "las_brisas": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Teatro"
          }
        },
        "26_02_2022": {
          "gotitas": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "cantores": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "alfareros": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "azulejos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sembradores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "las_brisas": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Yoga"
          }
        },
        "05_03_2022": {
          "gotitas": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "cantores": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "alfareros": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "azulejos": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "sembradores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "las_brisas": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Pintura"
          }
        },
        "12_03_2022": {
          "gotitas": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "cantores": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "alfareros": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "azulejos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sembradores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "las_brisas": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Fomento"
          }
        },
        "19_03_2022": {
          "gotitas": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "cantores": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "alfareros": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "azulejos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sembradores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "las_brisas": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Agroecologia"
          }
        },
        "26_03_2022": {
          "gotitas": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "cantores": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "alfareros": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "azulejos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sembradores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "las_brisas": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Cerámica"
          }
        },
        "02_04_2022": {
          "gotitas": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "cantores": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "alfareros": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "azulejos": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "sembradores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "las_brisas": {
            "drop_off_at": "Baile",
            "pick_up_at": "Baile"
          }
        },
        "09_04_2022": {
          "gotitas": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "cantores": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "alfareros": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "azulejos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sembradores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "las_brisas": {
            "drop_off_at": "Música",
            "pick_up_at": "Música"
          }
        },
        "16_04_2022": {
          "gotitas": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "cantores": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "alfareros": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "azulejos": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "sembradores": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "las_brisas": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          }
        },
        "23_04_2022": {
          "gotitas": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "cantores": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "alfareros": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "azulejos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sembradores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "las_brisas": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Teatro"
          }
        },
        "30_04_2022": {
          "gotitas": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "cantores": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "alfareros": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "azulejos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sembradores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "las_brisas": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Yoga"
          }
        },
        "07_05_2022": {
          "gotitas": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "cantores": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "alfareros": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "azulejos": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "sembradores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "las_brisas": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Pintura"
          }
        },
        "14_05_2022": {
          "gotitas": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "cantores": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "alfareros": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "azulejos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sembradores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "las_brisas": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Fomento"
          }
        },
        "21_05_2022": {
          "gotitas": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "cantores": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "alfareros": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "azulejos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sembradores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "las_brisas": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Agroecologia"
          }
        },
        "28_05_2022": {
          "gotitas": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "cantores": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "alfareros": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "azulejos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sembradores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "las_brisas": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Cerámica"
          }
        },
        "04_06_2022": {
          "gotitas": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "cantores": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "alfareros": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "azulejos": {
            "drop_off_at": "Agroecologia",
            "pick_up_at": "Teatro"
          },
          "sembradores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "las_brisas": {
            "drop_off_at": "Baile",
            "pick_up_at": "Baile"
          }
        },
        "11_06_2022": {
          "gotitas": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "cantores": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "alfareros": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "azulejos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sembradores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecologia"
          },
          "las_brisas": {
            "drop_off_at": "Música",
            "pick_up_at": "Música"
          }
        }
      },
      selectedDate: "",
      selectedGroup: "",
      groups: {
        gotitas: "Gotitas",
        cantores: "Cantores",
        alfareros: "Alfareros",
        azulejos: "Azulejos",
        sembradores: "Sembradores",
        las_brisas: "Las Brisas",
      },
      datesLabels: {
        "19_02_2022": {label: "Febrero 19", date: new Date(2022, 2 - 1, 19, 23, 59, 59)},
        "26_02_2022": {label: "Febrero 26", date: new Date(2022, 2 - 1, 26, 23, 59, 59)},
        "05_03_2022": {label: "Marzo 05", date: new Date(2022, 3 - 1, 5, 23, 59, 59)},
        "12_03_2022": {label: "Marzo 12", date: new Date(2022, 3 - 1, 12, 23, 59, 59)},
        "19_03_2022": {label: "Marzo 19", date: new Date(2022, 3 - 1, 19, 23, 59, 59)},
        "26_03_2022": {label: "Marzo 26", date: new Date(2022, 3 - 1, 26, 23, 59, 59)},
        "02_04_2022": {label: "Abril 02", date: new Date(2022, 4 - 1, 2, 23, 59, 59)},
        "09_04_2022": {label: "Abril 09", date: new Date(2022, 4 - 1, 9, 23, 59, 59)},
        "16_04_2022": {label: "Abril 16", date: new Date(2022, 4 - 1, 16, 23, 59, 59)},
        "23_04_2022": {label: "Abril 23", date: new Date(2022, 4 - 1, 23, 23, 59, 59)},
        "30_04_2022": {label: "Abril 30", date: new Date(2022, 4 - 1, 30, 23, 59, 59)},
        "07_05_2022": {label: "Mayo 07", date: new Date(2022, 5 - 1, 7, 23, 59, 59)},
        "14_05_2022": {label: "Mayo 14", date: new Date(2022, 5 - 1, 14, 23, 59, 59)},
        "21_05_2022": {label: "Mayo 21", date: new Date(2022, 5 - 1, 21, 23, 59, 59)},
        "28_05_2022": {label: "Mayo 28", date: new Date(2022, 5 - 1, 28, 23, 59, 59)},
        "04_06_2022": {label: "Junio 04", date: new Date(2022, 6 - 1, 4, 23, 59, 59)},
        "11_06_2022": {label: "Junio 11", date: new Date(2022, 6 - 1, 11, 23, 59, 59)},
      }
    }
  },
  computed: {
    activeDates() {
      return Object.entries(this.datesLabels).filter(d => d[1].date >= new Date())
    },
    firstDate() {
      return this.activeDates[0][0]
    },
  },
  mounted() {
    this.selectedDate = this.firstDate
  }
}
</script>

<style>
</style>
