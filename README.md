index.html# brbos-ai-a
AI Smart sales Management System
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BRBOS AI</title>

<style>
body {
    margin: 0;
    font-family: Arial;
    background: #101827;
    color: white;
}

header {
    background: #172438;
    padding: 22px;
    text-align: center;
}

header h1 {
    color: #00d9a5;
}

.container {
    padding: 18px;
}

.card {
    background: #1c2b40;
    padding: 20px;
    margin-bottom: 15px;
    border-radius: 12px;
}

.card h3 {
    color: #00d9a5;
}

input {
    width: 90%;
    padding: 13px;
    margin: 7px 0;
    border: none;
    border-radius: 8px;
}

button {
    background: #00b98b;
    color: white;
    border: none;
    padding: 12px 20px;
    border-radius: 8px;
    cursor: pointer;
}

.product {
    background: #263950;
    padding: 12px;
    margin: 8px 0;
    border-radius: 8px;
}
</style>
</head>

<body>

<header>
<h1>BRBOS AI</h1>
<p>نظام إدارة المبيعات الذكي</p>
</header>

<div class="container">

<div class="card">
<h3>مرحباً بك في BRBOS AI</h3>
<p>مركز التحكم الخاص بمتجرك</p>
</div>

<div class="card">
<h3>إحصائيات المتجر</h3>
<p>عدد المنتجات: <span id="count">0</span></p>
<p>المبيعات: قريباً</p>
<p>الأرباح: قريباً</p>
</div>

<div class="card">
<h3>إضافة منتج جديد</h3>

<input id="name" placeholder="اسم المنتج">

<input id="price" type="number"
placeholder="سعر المنتج">

<input id="quantity" type="number"
placeholder="الكمية">

<button onclick="addProduct()">
إضافة المنتج
</button>

</div>

<div class="card">
<h3>منتجات المتجر</h3>
<div id="products"></div>
</div>

<div class="card">
<h3>موظف المبيعات الذكي AI</h3>
<p id="aiStatus">
مساعدك الذكي سيكون متاحاً بعد ربط الذكاء الاصطناعي.
</p>
</div>

</div>

<script>

let products = JSON.parse(
localStorage.getItem("products") || "[]"
);

function displayProducts() {

document.getElementById("products").innerHTML = "";

products.forEach((p) => {

document.getElementById("products").innerHTML +=
`
<div class="product">
<strong>${p.name}</strong>
<br>
السعر: ${p.price}
<br>
الكمية: ${p.quantity}
</div>
`;

});

document.getElementById("count").innerText =
products.length;

}

function addProduct() {

let name = document.getElementById("name").value;
let price = document.getElementById("price").value;
let quantity = document.getElementById("quantity").value;

if (!name || !price || !quantity) {
alert("يرجى إدخال جميع البيانات");
return;
}

products.push({
name: name,
price: price,
quantity: quantity
});

localStorage.setItem(
"products",
JSON.stringify(products)
);

displayProducts();

document.getElementById("name").value = "";
document.getElementById("price").value = "";
document.getElementById("quantity").value = "";

alert("تمت إضافة المنتج بنجاح");

}

displayProducts();

</script>

</body>
</html>