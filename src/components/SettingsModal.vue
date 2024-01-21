<script setup lang="ts"></script>

<template>
  <div class="modal-mask">
    <div class="modal-container">
      <div class="modal-header">
        <slot name="header">Settings</slot>
      </div>

      <div class="modal-body">
        <slot name="body">
          <p>Settings</p>
        </slot>
      </div>
      <div class="modal-footer">
        <slot name="footer">
          <button>OK</button>
        </slot>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
