<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
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
    </div>
    <div class="row mt-3">
      <div class="col-12">
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
            <div class="col-12">Dejar en <strong><i>{{ dates[selectedDate][selectedGroup].drop_off_at }}</i></strong>
            </div>
            <div class="col-12">Recoger en <strong><i>{{ dates[selectedDate][selectedGroup].pick_up_at }}</i></strong>
            </div>
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
        "11_03_2023": {
          "saltamontes": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "colibries": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "enlazadores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "exploradores_creativos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          }
        },
        "18_03_2023": {
          "saltamontes": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "colibries": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "enlazadores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "exploradores_creativos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          }
        },
        "25_03_2023": {
          "saltamontes": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "colibries": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "enlazadores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "exploradores_creativos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          }
        },
        "01_04_2023": {
          "saltamontes": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "colibries": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "enlazadores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "exploradores_creativos": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          }
        },
        "08_04_2023": {
          "saltamontes": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "colibries": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "enlazadores": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "exploradores_creativos": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Semana Santa",
            "pick_up_at": "Semana Santa"
          }
        },
        "15_04_2023": {
          "saltamontes": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "colibries": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "enlazadores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "exploradores_creativos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          }
        },
        "22_04_2023": {
          "saltamontes": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "colibries": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "enlazadores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "exploradores_creativos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          }
        },
        "29_04_2023": {
          "saltamontes": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "colibries": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "enlazadores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "exploradores_creativos": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          }
        },
        "06_05_2023": {
          "saltamontes": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "colibries": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "enlazadores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "exploradores_creativos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          }
        },
        "13_05_2023": {
          "saltamontes": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "colibries": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "enlazadores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "exploradores_creativos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          }
        },
        "20_05_2023": {
          "saltamontes": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "colibries": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "enlazadores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "exploradores_creativos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          }
        },
        "27_05_2023": {
          "saltamontes": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "colibries": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "enlazadores": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "exploradores_creativos": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          }
        },
        "03_06_2023": {
          "saltamontes": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "colibries": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "enlazadores": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          },
          "exploradores_creativos": {
            "drop_off_at": "Cerámica",
            "pick_up_at": "Yoga"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          }
        },
        "10_06_2023": {
          "saltamontes": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "colibries": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "enlazadores": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          },
          "exploradores_creativos": {
            "drop_off_at": "Baile",
            "pick_up_at": "Pintura"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Yoga",
            "pick_up_at": "Cerámica"
          }
        },
        "17_06_2023": {
          "saltamontes": {
            "drop_off_at": "Teatro",
            "pick_up_at": "Agroecología"
          },
          "colibries": {
            "drop_off_at": "Agroecología",
            "pick_up_at": "Teatro"
          },
          "enlazadores": {
            "drop_off_at": "Fomento",
            "pick_up_at": "Música"
          },
          "exploradores_creativos": {
            "drop_off_at": "Música",
            "pick_up_at": "Fomento"
          },
          "sueno_de_lobos": {
            "drop_off_at": "Pintura",
            "pick_up_at": "Baile"
          }
        }
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
        "11_03_2023": {label: "Marzo 11", date: new Date(2023, 3 - 1, 11, 23, 59, 59)},
        "18_03_2023": {label: "Marzo 18", date: new Date(2023, 3 - 1, 18, 23, 59, 59)},
        "25_03_2023": {label: "Marzo 25", date: new Date(2023, 3 - 1, 25, 23, 59, 59)},
        "01_04_2023": {label: "Abril 1", date: new Date(2023, 4 - 1, 1, 23, 59, 59)},
        "08_04_2023": {label: "Abril 8", date: new Date(2023, 4 - 1, 8, 23, 59, 59)},
        "15_04_2023": {label: "Abril 15", date: new Date(2023, 4 - 1, 15, 23, 59, 59)},
        "22_04_2023": {label: "Abril 22", date: new Date(2023, 4 - 1, 22, 23, 59, 59)},
        "29_04_2023": {label: "Abril 29", date: new Date(2023, 4 - 1, 29, 23, 59, 59)},
        "06_05_2023": {label: "Mayo 6", date: new Date(2023, 5 - 1, 6, 23, 59, 59)},
        "13_05_2023": {label: "Mayo 13", date: new Date(2023, 5 - 1, 13, 23, 59, 59)},
        "20_05_2023": {label: "Mayo 20", date: new Date(2023, 5 - 1, 20, 23, 59, 59)},
        "27_05_2023": {label: "Mayo 27", date: new Date(2023, 5 - 1, 27, 23, 59, 59)},
        "03_06_2023": {label: "Junio 3", date: new Date(2023, 6 - 1, 3, 23, 59, 59)},
        "10_06_2023": {label: "Junio 10", date: new Date(2023, 6 - 1, 10, 23, 59, 59)},
        "17_06_2023": {label: "Junio 17", date: new Date(2023, 6 - 1, 17, 23, 59, 59)},
      },
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
