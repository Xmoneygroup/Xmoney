body {
    margin: 0;
    padding: 0;
    font-family: 'Montserrat', sans-serif;

    background: radial-gradient(circle at 20% 20%, #3a0ca3, #1a0933 40%, #000000 80%),
                radial-gradient(circle at 80% 80%, #4361ee, #1b1b2f 50%, #000000 90%);
    background-blend-mode: screen;
    background-attachment: fixed;

    position: relative;
    color: #fff;
    overflow-x: hidden;
}

/* --------------- SHTRESA YJEVE TË LËVIZSHËM --------------- */
body::before {
    content: "";
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background-image: url("https://www.transparenttextures.com/patterns/stardust.png");
    opacity: 0.20;
    animation: starsMove 18s linear infinite;
    pointer-events: none;
}

@keyframes starsMove {
    0% { transform: translateY(0); }
    100% { transform: translateY(-300px); }
}
/* ---------------------------------------------------------- */

/* TEKST FANTASTIK NEON */
.hero-text {
    font-family: 'Cinzel', serif;
    font-size: 90px;
    font-weight: 700;
    color: #ffffff;
    margin: 40px 0 0 50px;

    text-shadow: 0 0 15px #7b2ff7, 0 0 25px #5a189a, 0 0 40px #3a0ca3;

    opacity: 0;
    transform: translateX(-120px);
    animation: slideIn 1.6s ease-out forwards;
}

.subtext {
    font-size: 22px;
    font-weight: 300;
    max-width: 700px;
    margin: 20px 0 0 55px;
    line-height: 1.6;

    opacity: 0;
    transform: translateX(-120px);
    animation: fadeText 5s ease-out forwards;
}

@keyframes slideIn {
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

@keyframes fadeText {
    0% { opacity: 0; transform: translateX(-120px); }
    100% { opacity: 1; transform: translateX(0); }
}

/* -------------- KARTAT MODERNE 3D ---------------- */
.cards {
    display: flex;
    justify-content: center;
    gap: 35px;
    margin-top: 100px;
}

.card {
    background: rgba(255, 255, 255, 0.10);
    padding: 30px;
    width: 330px;
    height: 300px;
    border-radius: 18px;
    backdrop-filter: blur(12px);
    box-shadow: 0 10px 25px rgba(0,0,0,0.6);

    transition: transform 0.4s ease, box-shadow 0.4s ease;
    transform-style: preserve-3d;
}

/* Efekt 3D kur lëviz miu mbi kartë */
.card:hover {
    transform: translateY(-15px) rotateX(8deg) rotateY(-8deg);
    box-shadow: 0 20px 40px rgba(0,0,0,0.8);
}

/* -------------- BUTON NEON ---------------- */
.btn {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 14px 0;
    text-decoration: none;

    background: linear-gradient(90deg, #3feea9, #28a745);
    color: white;

    font-size: 17px;
    font-weight: 700;
    border-radius: 10px;

    box-shadow: 0 0 12px #28a745, 0 0 20px #28a745;

    transition: 0.35s ease;
}

.btn:hover {
    background: linear-gradient(90deg, #2ecc71, #1e8d43);
    box-shadow: 0 0 20px #2ecc71, 0 0 40px #2ecc71;
    transform: scale(1.05);
}
