<template>
  <div>
    <Table
      :columns="columns"
      :rows="tableData"
      rowKey="id"
      :selectable="true"
      :selectAllChecked="selectAllChecked"
      :someSelected="someSelected"
      @select-all="handleSelectAll"
      @select-row="handleRowSelect"
      tableClass="error-table"
      @cell-click="handleCellClick"
    />
    <SideModal
      v-if="isModalOpen"
      :data="selectedRowData"
      @close="isModalOpen = false"
    />
  </div>
</template>

<script>
import Table from "./common/Table.vue";
import SideModal from "../components/common/SideModal.vue";
export default {
  name: "DataTable",
  components: {
    Table,
    SideModal,
  },
  data() {
    return {
      selectAllChecked: false,
      someSelected: false,
      isModalOpen: false,
      selectedRowData: null,
      columns: [
        { label: "Дата и время", key: "dateTime" },
        { label: "Устройство", key: "device" },
        { label: "Тип ошибки", key: "errorType" },
        { label: "Текст ошибки", key: "errorText" },
      ],
      tableData: [
        {
          id: 1,
          dateTime: "20.01.24 14:08:12",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры ХОТ ГАЗ",
          selected: false,
        },
        {
          id: 2,
          dateTime: "13:23:30",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 3,
          dateTime: "12:45:45",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Эрв/Трв Авария",
          selected: false,
        },
        {
          id: 4,
          dateTime: "12:38:56",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария высокое давление",
          selected: false,
        },
        {
          id: 5,
          dateTime: "11:16:34",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 6,
          dateTime: "10:24:56",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 7,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 8,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 9,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 10,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 11,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 12,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 13,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 14,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 15,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
        {
          id: 16,
          dateTime: "10:04:16",
          device: "9000000004",
          errorType: "Ошибка",
          errorText: "Авария датчика температуры Жидкого фреона",
          selected: false,
        },
      ],
    };
  },
  methods: {
    handleRowSelect(row) {
      const rowIndex = this.tableData.findIndex((item) => item.id === row.id);

      if (rowIndex !== -1) {
        this.tableData[rowIndex].selected = !this.tableData[rowIndex].selected;
        this.updateSelectAllState();
        this.tableData = [...this.tableData];
      }
    },
    handleSelectAll(selected) {
      this.tableData.forEach((row) => {
        if ([1, 2, 3, 5].includes(row.id)) {
          row.selected = selected;
        }
      });

      this.tableData = [...this.tableData];
      this.someSelected = true;
      this.selectAllChecked = false;
    },
    updateSelectAllState() {
      const rowsToCheck = this.tableData.filter((row) =>
        [1, 2, 3, 5].includes(row.id)
      );

      const selectedCount = rowsToCheck.filter((row) => row.selected).length;
      const totalRows = rowsToCheck.length;

      this.selectAllChecked = selectedCount === totalRows;

      this.someSelected = selectedCount > 0 && selectedCount < totalRows;

      if (selectedCount === 0) {
        this.selectAllChecked = false;
        this.someSelected = false;
      }
    },

    handleCellClick(row, key) {
      if (key === "device") {
        this.selectedRowData = { ...row };
        this.isModalOpen = true;
      }
    },
  },
};
</script>

<style>
.error-table tbody tr td:nth-child(3) {
  color: #0072c0;
  cursor: pointer;
}
</style>
