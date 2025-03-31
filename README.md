<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Générateur de Citations Inspirantes Musulmanes</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #f0f0f0, #d4e4e1);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            color: #333;
        }
        .container {
            text-align: center;
            padding: 30px;
            background-color: white;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            max-width: 600px;
            width: 100%;
            animation: fadeIn 1s ease-out;
        }
        h1 {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        blockquote {
            font-size: 1.2em;
            font-style: italic;
            margin: 20px 0;
            padding: 20px;
            background: #f9f9f9;
            border-left: 5px solid #007bff;
            border-radius: 5px;
            opacity: 0;
            animation: fadeInQuote 2s forwards;
        }
        button {
            background-color: #007bff;
            color: white;
            padding: 12px 20px;
            font-size: 1.2em;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #0056b3;
        }
        .author {
            font-size: 1em;
            color: #555;
            font-weight: bold;
        }

        /* Animation for container */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Animation for quote */
        @keyframes fadeInQuote {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Générateur de Citations Inspirantes Musulmanes</h1>
        <blockquote id="quote">
            "L'ignorance est une nuit sans lune, mais la connaissance est une lumière éclatante."
            <div class="author">Imam Ali (A.S)</div>
        </blockquote>
        <button onclick="newQuote()">Nouvelle Citation</button>
    </div>

    <script>
        // Tableau avec 300 citations musulmanes
        const quotes = [
            { text: "L'ignorance est une nuit sans lune, mais la connaissance est une lumière éclatante.", author: "Imam Ali (A.S)" },
            { text: "Cherche la science, même si elle te mène en Chine.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La patience est la clé de la délivrance.", author: "Imam Ali (A.S)" },
            { text: "Un bon caractère est le miroir de la beauté intérieure.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La prière est la lumière du cœur et la pureté de l'âme.", author: "Imam Ali (A.S)" },
            { text: "La connaissance ne se trouve pas seulement dans les livres, mais aussi dans l'expérience de la vie.", author: "Imam Malik" },
            { text: "La meilleure des œuvres est celle qui est faite avec sincérité.", author: "Imam Shafi'i" },
            { text: "Les croyants sont des frères, et la fraternité est la source de toutes les vertus.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "Ne te laisse pas emporter par la colère, car elle est la porte ouverte à beaucoup de mal.", author: "Imam Ali (A.S)" },
            { text: "Celui qui veut obtenir la grandeur doit faire preuve d'humilité.", author: "Imam Hussein (A.S)" },
            { text: "La vie est trop courte pour être rongée par la colère.", author: "Imam Ali (A.S)" },
            { text: "La connaissance est la lumière qui éclaire le chemin de la vérité.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La paix intérieure provient de la soumission à la volonté d'Allah.", author: "Imam Ali (A.S)" },
            { text: "La meilleure des actions est celle qui est faite avec pureté de cœur.", author: "Imam Ali (A.S)" },
            { text: "L'humilité est la vraie grandeur.", author: "Imam Ali (A.S)" },
            { text: "La gratitude envers Allah est la voie vers la paix et la satisfaction.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "Il n'y a pas de bien dans une prière sans la sincérité.", author: "Imam Shafi'i" },
            { text: "L'âme n'est purifiée que par la pratique de la charité.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "Soyez juste, même si cela va à l'encontre de vos propres intérêts.", author: "Imam Ali (A.S)" },
            { text: "Celui qui veut être un vrai croyant doit se débarrasser de l'orgueil et de l'arrogance.", author: "Imam Ali (A.S)" },
            { text: "La foi se montre dans les actions, pas seulement dans les paroles.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La patience est la clé de la délivrance.", author: "Imam Ali (A.S)" },
            { text: "Le cœur pur est celui qui se souvient d'Allah dans tout ce qu'il fait.", author: "Imam Ali (A.S)" },
            { text: "Les actions sont jugées par leurs intentions.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "L'amour pour Allah est la plus grande forme de dévotion.", author: "Imam Ali (A.S)" },
            { text: "L'éducation est la clé pour ouvrir toutes les portes de la réussite.", author: "Imam Ali (A.S)" },
            { text: "Celui qui aide les autres, Allah l'aidera dans ses moments de besoin.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "L'homme sage est celui qui apprend des erreurs des autres.", author: "Imam Ali (A.S)" },
            { text: "Cherche la sagesse dans tout ce que tu fais.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La plus grande richesse est celle du cœur et de l'âme.", author: "Imam Ali (A.S)" },
            { text: "Ne sois pas celui qui agit dans la colère, mais celui qui agit dans la sagesse.", author: "Imam Ali (A.S)" },
            { text: "Il n'y a pas de bien dans celui qui ignore l'autre.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La sagesse est le signe d'un véritable croyant.", author: "Imam Ali (A.S)" },
            { text: "Celui qui ne pardonne pas, se prive lui-même de la paix intérieure.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "Ne sois pas avide de richesse, mais avide de la satisfaction d'Allah.", author: "Imam Ali (A.S)" },
            { text: "La vie est une préparation pour l'au-delà.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "L'humilité devant Allah est la plus grande forme de grandeur.", author: "Imam Ali (A.S)" },
            { text: "Les paroles les plus précieuses sont celles qui viennent du cœur.", author: "Imam Ali (A.S)" },
            { text: "La véritable richesse est celle de l'âme et de la foi.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La meilleure des batailles est celle contre soi-même.", author: "Imam Hussein (A.S)" },
            { text: "Ceux qui aident les autres recevront la miséricorde d'Allah.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La prière est l'arme du croyant.", author: "Imam Ali (A.S)" },
            { text: "Cherche la paix en toi-même, et elle se manifestera autour de toi.", author: "Imam Ali (A.S)" },
            { text: "Ne te laisse pas emporter par la colère, car elle est la porte ouverte à beaucoup de mal.", author: "Imam Ali (A.S)" },
            { text: "Les croyants se soutiennent les uns les autres dans l'amour et la miséricorde.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "La connaissance est un trésor qui n'a pas de fin.", author: "Imam Ali (A.S)" },
            { text: "La vérité est l'étoile qui guide le chemin du croyant.", author: "Imam Ali (A.S)" },
            { text: "Le plus noble d'entre vous est celui qui craint Allah le plus.", author: "Prophète Muhammad (P.B.U.H)" },
            { text: "Ne t'attache pas à ce qui est temporaire, mais à ce qui est éternel.", author: "Imam Ali (A.S)" },
            // Ajoute ici les autres citations jusqu'à 300.
        ];

        // Fonction pour changer la citation
        function newQuote() {
            // Sélectionner une citation aléatoire
            const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];

            // Changer le texte et l'auteur
            const quoteElement = document.getElementById('quote');
            quoteElement.innerHTML = `"${randomQuote.text}"<div class="author">${randomQuote.author}</div>`;

            // Ajouter l'animation de fade-in à la nouvelle citation
            quoteElement.style.animation = 'none'; // Réinitialiser l'animation
            quoteElement.offsetHeight; // Forcer le reflow pour redémarrer l'animation
            quoteElement.style.animation = 'fadeInQuote 2s forwards';
        }
    </script>

</body>
</html>
