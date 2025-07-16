# my-online-shop-

                                                                #HTML
<!DOCTYPE html> <html lang="hy"> <head>   <meta charset="UTF-8">   <title>Իմ Առցանց Խանութը</title>   <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">   <link rel="stylesheet" href="style.css"> </head> <body>   <!-- Navbar -->   <nav class="navbar navbar-expand-lg navbar-dark bg-dark">     <div class="container-fluid">       <a class="navbar-brand" href="#">Իմ Խանութը</a>     </div>   </nav>    <!-- Carousel -->   <div class="container mt-4">     <div id="carouselExample" class="carousel slide" data-bs-ride="carousel">       <div class="carousel-inner">         <div class="carousel-item active">           <img src="https://blog-frontend.envato.com/cdn-cgi/image/width=1850,quality=75,format=auto/uploads/sites/2/2023/01/Screen-Shot-2023-01-16-at-2.12.40-pm.png" class="d-block w-100" alt="...">         </div>         <div class="carousel-item">           <img src="https://plus.unsplash.com/premium_photo-1684785617500-fb22234eeedd?fm=jpg&q=60&w=3000" class="d-block w-100" alt="...">         </div>         <div class="carousel-item">           <img src="https://plus.unsplash.com/premium_photo-1664201890375-f8fa405cdb7d?fm=jpg&q=60&w=3000" class="d-block w-100" alt="...">         </div>         <div class="carousel-item">           <img src="https://plus.unsplash.com/premium_photo-1664201889922-66bc3c778c1e?fm=jpg&q=60&w=3000" class="d-block w-100" alt="...">         </div>       </div>       <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">         <span class="carousel-control-prev-icon"></span>       </button>       <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">         <span class="carousel-control-next-icon"></span>       </button>     </div>   </div>    <!-- Զամբյուղի icon-ը -->   <div class="cart-container">   <button class="cart-button">🛒     <span class="cart-count">0</span>   </button> </div>  <div class="cart-modal hidden">   <p></p> </div>  <!-- Modal պատուհանը --> <div class="cart-modal hidden"> </div>    <!-- Product Cards -->   <div class="container mt-4">     <div class="row row-cols-1 
                                                                                 #JS
const products = [
  { name: "Հեռախոս", price: 120000, img: "https://cdn.mos.cms.futurecdn.net/pxym4da6CU52RWHuBdRtqm.jpg" },
  { name: "Սառնարան", price: 95000, img: "https://vega.am/image/cache/catalog/Angel/Hrach/BERG%20BR-N317BX%204-540x400.jpg" },
  { name: "Լվացքի մեքենա", price: 87000, img: "https://vega.am/image/cache/catalog/1HRACH/2020/2021/2024/Hoktember/Lvacqi%20Meqena/F2V5HYLYJ%20(2)-540x400.jpg" },
  { name: "Համակարգիչ", price: 150000, img: "https://eldorado.am/media/catalog/product/cache/f8f376667ef841560f3ecb714414579d/h/p/hp_laptop_sebastian_23c1_core_i3-1315u_8gb_512gb_pcie_value_7p4n8e_4.jpg" },
  { name: "Տոստեր", price: 25000, img: "https://vega.am/image/cache/catalog/1HRACH/2020/2021/2025/Petrvar/Toster/CT-1423%20(3)-540x400.jpg" },
  { name: "Հարիչ", price: 18000, img: "https://eldorado.am/media/catalog/product/cache/b636eac9f5e866652b5cbe8cee86d97c/k/i/kitchenaid_5ksm125eer_artisan.jpg" },
  { name: "Միկրոալիքային վառարան", price: 40000, img: "https://vega.am/image/cache/catalog/1HRACH/2020/2021/2025/Mart/Mikroaliqayin%20Vararan/PANASONIC%20NN-ST25HBZPE%20%20(3)-540x400.jpg" },
  { name: "Արդուկ", price: 9500, img: "https://vivaelectronics.am/Api/FetchImgBinBySKU/12883/%D1%83%D1%82%D1%8E%D0%B3-philips-da-dst7060-20.png" },
  { name: "Ականջակալ", price: 15000, img: "https://www.onshop.am/images/product/general/73d10e2cb03e1fc71fe8ff0f4248f580.jpg" },
  { name: "Հեռախոսի պատյան", price: 1500, img: "https://www.pacolipower.com/uploads/59-300x300.jpg" },
];

const container = document.getElementById("product-container");
const cartMessage = document.getElementById("cart-message");

products.forEach(product => {
  const col = document.createElement("div");
  col.className = "col";

  const card = document.createElement("div");
  card.className = "card h-100";
  card.innerHTML = `
    <img src="${product.img}" class="card-img-top" alt="${product.name}">
    <div class="card-body">
      <h5 class="card-title">${product.name}</h5>
      <p class="card-text">Գին՝ ${product.price} դրամ</p>
      <button class="btn btn-primary me-2" onclick="buyNow('${product.name}')">Գնել հիմա</button>
      <button class="add-to-cart">Ավելացնել զամբյուղ</button>
    </div>
  `;
const cartButton = document.querySelector('.cart-button');
const cartCount = document.querySelector('.cart-count');
const modal = document.querySelector('.cart-modal');
const addButtons = document.querySelectorAll('.add-to-cart');

let count = 0;

function addToCart() {
  count++;
  cartCount.textContent = count;

  modal.textContent = '';
  modal.classList.remove('hidden');

  // Փակենք պատուհանը 2 վայրկյանից
  setTimeout(() => {
    modal.classList.add('hidden');
  }, 2000);
}



// Սեղմում են "Ավելացնել զամբյուղ"
addButtons.forEach(button => {
  button.addEventListener('click', addToCart);
});
  col.appendChild(card);
  container.appendChild(col);
});

window.buyNow = function(name) {
  alert(`Դուք ընտրեցիք "${name}" ապրանքը։`);
};

  
const col = document.createElement("div");
col.className = "col";
col.appendChild(card);
container.appendChild(col);

                                                                    #CSS


.card-img-top {
  width: 100%;
  height: 300px;
  object-fit: cover;
}
.card {
  height: 100%;
}

.cart-container {
  position: absolute;
  top: 10px;
  right: 10px;
}

.cart-button {
  position: relative;
  font-size: 24px;
  background: none;
  border: none;
  cursor: pointer;
}

.cart-count {
  position: absolute;
  top: -5px;
  right: -5px;
  background-color: red;
  color: white;
  border-radius: 50%;
  padding: 2px 6px;
  font-size: 12px;
}

.cart-modal {
  position: fixed;
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 20px;
  border: 1px solid gray;
  box-shadow: 0 0 10px rgba(0,0,0,0.2);
  z-index: 1000;
}

.hidden {
  display: none;
}

.cart-count {
  position: absolute;
  top: -5px;
  right: -5px;
  background-color: crimson;
  color: white;
  border-radius: 50%;
  padding: 2px 6px;
  font-size: 12px;
  font-weight: bold;
}
