<template>
  <div class="container">
    <div class="row">
      <div class="col-6">
        <div class="form-floating">
          <select v-model="selectedDate" class="form-select form-select-lg" aria-label="Seleccione un día"
                  id="dateSelect">
            <option v-for="(date, index) in datesLabels" :value="index" :key="index">
              {{ date }}
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

      <section v-if="selectedDate !== ''">
        <div v-if="selectedGroup === ''" class="container">
          <div v-for="(group, index) in dates[selectedDate]" :key="index" class="row">
            <div class="col-12">
              <div class="row">
                <div class="col-12"><span>{{ groups[index] }}</span></div>
              </div>
              <div class="row">
                <div class="col-6">Dejar en {{ group.drop_off_at }}</div>
                <div class="col-6">Recoger en {{ group.pick_up_at }}</div>
              </div>
            </div>
          </div>
        </div>

        <div v-if="selectedGroup !== ''" class="container">
          <div class="row">
            <div class="col-12">
              <div class="row">
                <div class="col-12">
                  <span>{{ groups[selectedGroup] }}</span>
                </div>
              </div>
              <div class="row">
                <div class="col-6">Dejar en {{ dates[selectedDate][selectedGroup].drop_off_at }}</div>
                <div class="col-6">Recoger en {{ dates[selectedDate][selectedGroup].pick_up_at }}</div>
              </div>
            </div>
          </div>
        </div>
      </section>
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
        "19_02_2022": "Febrero 19",
        "26_02_2022": "Febrero 26",
        "05_03_2022": "Marzo 05",
        "12_03_2022": "Marzo 12",
        "19_03_2022": "Marzo 19",
        "26_03_2022": "Marzo 26",
        "02_04_2022": "Abril 02",
        "09_04_2022": "Abril 09",
        "16_04_2022": "Abril 16",
        "23_04_2022": "Abril 23",
        "30_04_2022": "Abril 30",
        "07_05_2022": "Mayo 07",
        "14_05_2022": "Mayo 14",
        "21_05_2022": "Mayo 21",
        "28_05_2022": "Mayo 28",
        "04_06_2022": "Junio 04",
        "11_06_2022": "Junio 11",
      }
    }
  },
}
</script>

<style>
</style>
