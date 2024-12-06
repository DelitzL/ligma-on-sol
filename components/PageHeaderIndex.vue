<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  subtitle: {
    type: String,
    required: false,
  },
  btntext: {
    type: String,
    required: true,
  },
  imageSrc: {
    type: String,
    required: false,
  },
});
</script>


<template>
    <div class="page-header">
      <div class="two-column-layout">
        <!-- Left Column: Image -->
        <div class="column image-column">
          <img :src="imageSrc" alt="Image" class="responsive-image" />
        </div>
  
        <!-- Right Column: Text -->
        <div class="page-header-padding">
          <div class="column text-column">
            <p class="slogan">Earn Now With</p>
            <p class="title">{{ title }}</p>
            <p class="subtitle">{{ subtitle }}</p>
            <div class="button-container">
              <button class="glow-on-hover" type="button">{{ btntext }}</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  

  <style scoped>
  .two-column-layout {
    display: flex;
    gap: 20px; /* Space between columns */
    align-items: center;
  }
  
  .column {
    flex: 1; /* Each column takes up equal space */
  }
  
  .image-column {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .responsive-image {
    width: 100%; /* Occupy full width of the column */
    max-width: 600px; /* Limit the maximum width of the image */
    height: auto; /* Maintain aspect ratio */
    border-radius: 8px; /* Optional rounded corners */
  }
  
  .text-column {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center; /* Center-align the text */
    align-items: center; /* Center content horizontally */
  }
  
  .page-header {
    text-align: left;
    background-color: var(--color-primary);
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.5);
  }
  
  .page-header-padding {
    padding: 50px 50px 50px 0px;
  }
  
  .button-container {
    padding: 20px 0;
  }
  
  p.title {
    font-size: 80px;
  }
  
  p.subtitle {
    font-size: 20px; /* Add font size for subtitle */
  }
  
  /* Responsive Adjustments for Smaller Screens */
  @media (max-width: 1269px) and (max-height: 806px) {
    .two-column-layout {
      flex-direction: column; /* Stack columns vertically */
      text-align: center; /* Center-align content */
    }
  
    .image-column {
      order: -1; /* Ensure the image appears above the text */
      margin-bottom: 20px; /* Add spacing between image and text */
    }
  
    .responsive-image {
      max-width: 90%; /* Reduce image size slightly for smaller screens */
    }
  
    p.title {
      font-size: 40px; /* Adjust text size for smaller screens */
    }
  }

  /* Button CSS */
  html,
body {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    background: #000;
}

.glow-on-hover {
    width: 220px;
    height: 50px;
    border: none;
    outline: none;
    color: #fff;
    background: #111;
    cursor: pointer;
    position: relative;
    z-index: 0;
    border-radius: 10px;
}

.glow-on-hover:before {
    content: '';
    background: linear-gradient(45deg, #ff0000, #ff7300, #fffb00, #48ff00, #00ffd5, #002bff, #7a00ff, #ff00c8, #ff0000);
    position: absolute;
    top: -2px;
    left:-2px;
    background-size: 400%;
    z-index: -1;
    filter: blur(5px);
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    animation: glowing 20s linear infinite;
    opacity: 0;
    transition: opacity .3s ease-in-out;
    border-radius: 10px;
}

.glow-on-hover:active {
    color: #000
}

.glow-on-hover:active:after {
    background: transparent;
}

.glow-on-hover:hover:before {
    opacity: 1;
}

.glow-on-hover:after {
    z-index: -1;
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: #111;
    left: 0;
    top: 0;
    border-radius: 10px;
}

@keyframes glowing {
    0% { background-position: 0 0; }
    50% { background-position: 400% 0; }
    100% { background-position: 0 0; }
}
  </style>
  
  
