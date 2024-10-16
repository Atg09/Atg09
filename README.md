<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Números Primos</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="primeDisplay">2</div>
    <script src="script.js"></script>
</body>
</html>
body {
    background-color: black;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

#primeDisplay {
    color: white;
    font-size: 100px;
    text-align: center;
}
let primes = [2];
let currentIndex = 0;

function isPrime(num) {
    if (num <= 1) return false;
    for (let i = 2; i <= Math.sqrt(num); i++) {
        if (num % i === 0) return false;
    }
    return true;
}

function nextPrime() {
    let num = primes[primes.length - 1] + 1;
    while (!isPrime(num)) {
        num++;
    }
    primes.push(num);
    return num;
}

document.getElementById('primeDisplay').innerText = primes[currentIndex];

document.addEventListener('click', (event) => {
    if (event.button === 0) { // Click izquierdo
        currentIndex++;
        if (currentIndex >= primes.length) {
            const next = nextPrime();
            document.getElementById('primeDisplay').innerText = next;
        } else {
            document.getElementById('primeDisplay').innerText = primes[currentIndex];
        }
    } else if (event.button === 2) { // Click derecho
        if (currentIndex > 0) {
            currentIndex--;
            document.getElementById('primeDisplay').innerText = primes[currentIndex];
        }
    }
});

document.addEventListener('contextmenu', (event) => {
    event.preventDefault(); // Evitar el menú contextual del clic derecho
});



