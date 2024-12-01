<template>
    <footer class="footer">
        <div class="grid grid-cols-3 gap-4">
            <div>01</div>
            <div>01</div>
            <div>01</div>
        </div>
    </footer>
  </template>


  <style scoped>
.footer {
  background-color: var(--color-secondary);
  color: var(--color-light);
  padding: 10px 20px;
  width: 100%;
}

.footer-container {
  display: flex;
  align-items: center;
  justify-content: space-between; /* Spread items across the footer */
  max-width: 1200px; /* Keep content centered */
  margin: 0 auto; /* Center container */
  padding: 0 20px;
}

.footer-left {
  flex: 1; /* Take up equal space */
  text-align: left; /* Align text to the left */
}

.footer-center {
  flex: 1; /* Take up equal space */
  text-align: center; /* Center text */
}

.footer-right {
  flex: 1; /* Take up equal space */
  display: flex;
  justify-content: flex-end; /* Align icon to the right */
}

@media (max-width: 768px) {
  .footer-container {
    flex-direction: column; /* Stack items vertically */
    text-align: center; /* Center all text */
  }
}

  .footer-left,
  .footer-center,
  .footer-right {
    flex: unset; /* Remove flex properties for stacking */
    margin-bottom: 10px; /* Add spacing between stacked items */
  }

  .footer-right {
    justify-content: center; /* Center the icon in the stacked layout */
  }

</style>