<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CarSell - Buy & Sell Cars Online</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Header -->
    <header>
        <div class="logo">CarSell</div>
        <nav>
            <a href="#">Home</a>
            <a href="#">Buy</a>
            <a href="#">Sell</a>
            <a href="#">About Us</a>
            <a href="#">Contact</a>
        </nav>
    </header>

    <!-- Search Section -->
    <section class="search-section">
        <h1>Find Your Perfect Car</h1>
        <form id="searchForm">
            <input type="text" placeholder="Search by make, model, or keyword" id="searchInput">
            <button type="submit">Search</button>
        </form>
    </section>

    <!-- Car Listings Section -->
    <section id="carListings" class="listings">
        <!-- Car items will be dynamically added here -->
    </section>

    <script src="script.js"></script>
</body>
</html>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    box-sizing: border-box;
    background-color: #f4f4f4;
}

/* Header */
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #0a4d8b;
    color: white;
    padding: 10px 20px;
}

header .logo {
    font-size: 1.8rem;
    font-weight: bold;
}

header nav a {
    color: white;
    text-decoration: none;
    margin-left: 15px;
}

/* Search Section */
.search-section {
    text-align: center;
    padding: 30px;
    background-color: white;
    margin-bottom: 20px;
}

.search-section input {
    padding: 10px;
    width: 300px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.search-section button {
    padding: 10px 20px;
    background-color: #0a4d8b;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 5px;
}

.search-section button:hover {
    background-color: #083a68;
}

/* Car Listings */
.listings {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 20px;
}

.listing-item {
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 10px;
    text-align: center;
}

.listing-item img {
    width: 100%;
    border-radius: 5px;
}

.listing-item h3 {
    color: #0a4d8b;
}
// Sample Car Data
const cars = [
    {
        id: 1,
        make: 'Toyota',
        model: 'Corolla',
        year: 2020,
        price: '$15,000',
        image: 'https://via.placeholder.com/250'
    },
    {
        id: 2,
        make: 'Ford',
        model: 'Mustang',
        year: 2021,
        price: '$35,000',
        image: 'https://via.placeholder.com/250'
    },
    {
        id: 3,
        make: 'BMW',
        model: 'X5',
        year: 2019,
        price: '$45,000',
        image: 'https://via.placeholder.com/250'
    }
];

// Function to display cars
function displayCars(carList) {
    const listings = document.getElementById('carListings');
    listings.innerHTML = '';

    carList.forEach(car => {
        const carElement = document.createElement('div');
        carElement.classList.add('listing-item');
        carElement.innerHTML = `
            <img src="${car.image}" alt="${car.make} ${car.model}">
            <h3>${car.make} ${car.model}</h3>
            <p>Year: ${car.year}</p>
            <p>Price: ${car.price}</p>
        `;
        listings.appendChild(carElement);
    });
}

// Display all cars on page load
displayCars(cars);

// Search functionality
document.getElementById('searchForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const query = document.getElementById('searchInput').value.toLowerCase();

    const filteredCars = cars.filter(car =>
        car.make.toLowerCase().includes(query) ||
        car.model.toLowerCase().includes(query) ||
        car.year.toString().includes(query)
    );

    displayCars(filteredCars);
});
