// Бургер-меню
const menuToggle = document.querySelector('.menu-toggle');
const navList = document.querySelector('.nav-list');

menuToggle.addEventListener('click', () => {
    navList.classList.toggle('active');
    menuToggle.classList.toggle('active');
});

// Слайдер
const slides = document.querySelectorAll('.slide');
const prevBtn = document.querySelector('.prev');
const nextBtn = document.querySelector('.next');
let currentSlide = 0;

function showSlide(n) {
    slides.forEach(slide => slide.classList.remove('active'));
    currentSlide = (n + slides.length) % slides.length;
    slides[currentSlide].classList.add('active');
}

prevBtn.addEventListener('click', () => showSlide(currentSlide - 1));
nextBtn.addEventListener('click', () => showSlide(currentSlide + 1));

// Автопереключение слайдов
setInterval(() => showSlide(currentSlide + 1), 5000);

// Темная/светлая тема
const themeToggle = document.getElementById('theme-toggle');
const html = document.documentElement;

themeToggle.addEventListener('click', () => {
    html.dataset.theme = html.dataset.theme === 'light' ? 'dark' : 'light';
    themeToggle.innerHTML = html.dataset.theme === 'light' 
        ? '<i class="fas fa-moon"></i>' 
        : '<i class="fas fa-sun"></i>';
});

// Модальное окно корзины
const cartButtons = document.querySelectorAll('.add-to-cart');
const modal = document.getElementById('cart-modal');
const closeBtn = document.querySelector('.close');
const cartItems = document.getElementById('cart-items');
const totalElement = document.querySelector('.total span');

let cart = [];
let total = 0;

cartButtons.forEach(button => {
    button.addEventListener('click', () => {
        const product = button.getAttribute('data-product');
        const price = parseInt(button.previousElementSibling.textContent);
        
        cart.push({ product, price });
        total += price;
        
        updateCart();
        modal.style.display = 'block';
    });
});

closeBtn.addEventListener('click', () => {
    modal.style.display = 'none';
});

window.addEventListener('click', (e) => {
    if (e.target === modal) {
        modal.style.display = 'none';
    }
});

function updateCart() {
    cartItems.innerHTML = '';
    cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.product} - ${item.price} руб.`;
        cartItems.appendChild(li);
    });
    totalElement.textContent = total;
}
