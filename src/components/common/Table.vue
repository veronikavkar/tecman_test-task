<template>
  <div class="table-container">
    <div class="filters-container">
      <div class="filters">
        <FilterButton
          label="КОЛОНКИ"
          icon="columns.svg"
          :onClickAction="openColumnFilter"
        />
        <FilterButton
          label="ФИЛЬТРОВАТЬ"
          icon="filters.svg"
          :filterCount="activeFilters"
          :onClickAction="openDataFilter"
        />
      </div>
      <div class="search">
        <SearchInput />
      </div>
    </div>
    <table :class="tableClass">
      <thead>
        <tr>
          <th v-if="selectable">
            <!-- Чекбокс для выбора всех строк -->
            <CustomCheckbox
              :modelValue="selectAllChecked"
              :indeterminate="someSelected"
              @update:modelValue="$emit('select-all', $event)"
            />
          </th>
          <th v-for="col in columns" :key="col.key">{{ col.label }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="row in rows" :key="row[rowKey]" class="checkbox-cell">
          <td v-if="selectable">
            <!-- Чекбокс для выбора конкретной строки -->
            <CustomCheckbox
              :modelValue="row.selected"
              @update:modelValue="$emit('select-row', row)"
            />
          </td>
          <td
            v-for="col in columns"
            :key="col.key"
            @click="$emit('cell-click', row, col.key)"
            :class="{ clickable: col.key === 'device' }"
          >
            {{ row[col.key] }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import CustomCheckbox from "../common/CustomCheckbox.vue";
import FilterButton from "../common/FilterButton.vue";
import SearchInput from "../common/SearchInput.vue";

export default {
  name: "Table",

  components: {
    CustomCheckbox,
    FilterButton,
    SearchInput,
  },
  props: {
    columns: {
      type: Array,
      required: true,
    },
    rows: {
      type: Array,
      required: true,
    },
    rowKey: {
      type: String,
      required: true,
    },
    selectable: {
      type: Boolean,
      default: false,
    },
    tableClass: {
      type: String,
      default: "",
    },
    selectAllChecked: {
      type: Boolean,
      default: false,
    },
    someSelected: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped>
.filters-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}
.filters {
  display: flex;
  gap: 13px;
}
.table-container {
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.1);
  padding: 16px 17px;
}

table {
  width: 100%;
  border-collapse: collapse;
}
tr {
  height: 44px;
}
th {
  font-weight: 500;
}
th,
td {
  padding: 8px 12px;
  text-align: left;
  font-size: 14px;
  vertical-align: middle;
}
th:first-child,
td:first-child {
  padding-left: 0;
  padding-right: 0;
  width: 40px;
  height: 32px;
}
.checkbox-cell {
  text-align: center;
  vertical-align: middle;
  padding: 0;
}
</style>
