<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vente d'Unités chez Alexis</title>
    <style>
        /* STYLE GÉNÉRAL ET POLICE MODERNE */
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@800&family=Poppins:wght@300;400;600&display=swap');

        body {
            font-family: 'Poppins', sans-serif;
            /* ARRIÈRE-PLAN AVEC DÉGRADÉ ROYAL */
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 10px;
        }

        .container {
            background: rgba(255, 255, 255, 0.95);
            width: 100%;
            max-width: 450px;
            border-radius: 25px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            overflow: hidden;
            padding-bottom: 20px;
        }

        /* TITRE ORANGE AVEC POLICE STYLEE ET ANIMATION */
        header {
            background-color: #FF8C00;
            padding: 30px 15px;
            text-align: center;
            color: white;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        h1 {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.5rem;
            margin: 0;
            text-transform: uppercase;
            letter-spacing: 2px;
            animation: floating 3s ease-in-out infinite;
        }

        @keyframes floating {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        .logo-airtel {
            width: 70px;
            margin-top: 15px;
            filter: drop-shadow(0px 4px 6px rgba(0,0,0,0.2));
        }

        .intro {
            padding: 15px;
            font-size: 0.85rem;
            color: #444;
            text-align: center;
            background: #fff5e6;
            margin: 15px;
            border-radius: 12px;
            border-left: 5px solid #FF8C00;
        }

        .form-content { padding: 0 20px; }

        .field { margin-bottom: 15px; position: relative; }
        label { display: block; font-weight: 600; font-size: 0.9rem; margin-bottom: 5px; color: #333; }

        input {
            width: 100%;
            padding: 14px;
            border-radius: 10px;
            border: 2px solid transparent;
            font-family: 'Poppins', sans-serif;
            box-sizing: border-box;
            transition: 0.3s;
            font-size: 1rem;
        }

        .field-nom input { background: #e3f2fd; border-color: #2196f3; }
        .field-choix input { background: #e8f5e9; border-color: #4caf50; }
        .field-numero input { background: #fffde7; border-color: #fbc02d; }

        /* CHAMP MONTANT AVEC FC BLOQUÉ */
        .montant-container { position: relative; display: flex; align-items: center; }
        .montant-container input { background: #f3e5f5; border-color: #9c27b0; padding-right: 50px; }
        .fc-suffix { position: absolute; right: 15px; font-weight: 800; color: #9c27b0; pointer-events: none; }

        /* BOUTONS PRODUITS ET DURÉE */
        .btn-group {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin: 10px 0;
        }

        .btn-prod, .btn-time {
            padding: 12px 5px;
            border: none;
            border-radius: 8px;
            color: white;
            font-weight: bold;
            font-size: 0.8rem;
            cursor: pointer;
            transition: 0.3s;
            opacity: 0.6;
        }

        .btn-prod.active, .btn-time.active {
            opacity: 1;
            transform: scale(1.05);
            box-shadow: 0 5px 12px rgba(0,0,0,0.2);
            outline: 2px solid #333;
        }

        .p1 { background: #E91E63; } /* Méga */
        .p2 { background: #00BCD4; } /* Munité */
        .p3 { background: #8BC34A; } /* GB 24H */
        .p4 { background: #FF9800; } /* GB 48H */
        .p5 { background: #673AB7; } /* Unité */
        .p6 { background: #2196f3; } /* SMS */
        .t-btn { background: #607d8b; }

        .hidden { display: none; }

        /* BOUTON ENVOYER */
        .submit-btn {
            width: 100%;
            padding: 16px;
            background: #28a745;
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: 800;
            cursor: pointer;
            margin-top: 15px;
            transition: 0.3s;
            box-shadow: 0 5px 15px rgba(40, 167, 69, 0.3);
        }

        .submit-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            box-shadow: none;
            transform: scale(1) !important;
        }

        /* POPUP */
        .overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.85);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 100;
        }

        .popup {
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            max-width: 300px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        }

        .popup img { width: 80px; margin-bottom: 15px; }

    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>VENTE D’UNITÉS AIRTEL MONEY CHEZ ALEXIS</h1>
        <img src="https://github.com/user-attachments/assets/544faacf-037d-48db-91b0-343ccb49273e" />

    <div class="intro">
        Si tu veux qu’Alexis t’envoie des méga, des unités, des minutes ou des SMS, sois prêt à payer, car ce travail n’est pas gratuit.
    </div>

    <div class="form-content">
        <div id="section-produits">
            <label>1. Choisissez votre produit :</label>
            <div class="btn-group">
                <button class="btn-prod p1" onclick="selectProd('Méga', this)">Méga</button>
                <button class="btn-prod p2" onclick="selectProd('Munité', this)">Munité</button>
                <button class="btn-prod p3" onclick="selectProd('GB 24H', this)">GB 24H</button>
                <button class="btn-prod p4" onclick="selectProd('GB 48H', this)">GB 48H</button>
                <button class="btn-prod p5" onclick="selectProd('Unité', this)">Unité</button>
                <button class="btn-prod p6" onclick="selectProd('SMS', this)">SMS</button>
            </div>
        </div>

        <div id="section-duree" class="hidden">
            <label>2. Choisissez la durée (Obligatoire pour SMS) :</label>
            <div class="btn-group">
                <button class="btn-time t-btn" onclick="selectTime('2 jours', this)">2 jours</button>
                <button class="btn-time t-btn" onclick="selectTime('5 jours', this)">5 jours</button>
                <button class="btn-time t-btn" onclick="selectTime('7 jours', this)">7 jours</button>
                <button class="btn-time t-btn" onclick="selectTime('30 jours', this)">30 jours</button>
            </div>
        </div>

        <div class="field field-choix">
            <label>3. Écrire votre choix (Nombre d'unités/SMS) :</label>
            <input type="text" id="choix" placeholder="Ex: 50 unités" oninput="checkInput()">
        </div>

        <div class="field field-nom">
            <label>4. Votre Nom :</label>
            <input type="text" id="nom" placeholder="Entrez votre nom" oninput="checkInput()">
        </div>

        <div class="field field-montant">
            <label>5. Montant à payer :</label>
            <div class="montant-container">
                <input type="number" id="montant" placeholder="Ex: 500" oninput="checkInput()">
                <span class="fc-suffix">FC</span>
            </div>
        </div>

        <div class="field field-numero">
            <label>6. Votre Numéro Airtel :</label>
            <input type="tel" id="numero" placeholder="09..." oninput="checkInput()">
        </div>

        <button id="submitBtn" class="submit-btn" onclick="envoyerSMS()" disabled>Envoyer un message</button>
    </div>
</div>

<div class="overlay" id="overlay">
    <div class="popup">
        <img src="https://cdn-icons-png.flaticon.com/512/148/148767.png" alt="Succès">
        <p><strong>Vous avez envoyé un message pour acheter un produit chez Alexis.</strong></p>
        <button onclick="fermerPopup()" style="background:#FF8C00; color:white; border:none; padding:10px 20px; border-radius:5px; cursor:pointer;">OK</button>
    </div>
</div>

<script>
    let dureeSelectionnee = "N/A"; 
    let produitSelectionne = "";

    function selectProd(val, btn) {
        produitSelectionne = val;
        document.querySelectorAll('.btn-prod').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        
        const sectionDuree = document.getElementById('section-duree');
        if(val === 'SMS') {
            sectionDuree.classList.remove('hidden');
            dureeSelectionnee = ""; // Force le choix de la durée pour le SMS
        } else {
            sectionDuree.classList.add('hidden');
            dureeSelectionnee = "Standard"; // Pas besoin de durée pour les autres
        }
        checkInput();
    }

    function selectTime(val, btn) {
        dureeSelectionnee = val;
        document.querySelectorAll('.btn-time').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        checkInput();
    }

    function checkInput() {
        const nom = document.getElementById('nom').value;
        const choix = document.getElementById('choix').value;
        const montant = document.getElementById('montant').value;
        const numero = document.getElementById('numero').value;
        const btn = document.getElementById('submitBtn');

        // Le bouton s'active si tous les champs sont remplis ET qu'une durée est choisie si c'est un SMS
        if(nom && choix && montant && numero && produitSelectionne && dureeSelectionnee !== "") {
            btn.disabled = false;
        } else {
            btn.disabled = true;
        }
    }

    function envoyerSMS() {
        const nom = document.getElementById('nom').value;
        const choix = document.getElementById('choix').value;
        const montant = document.getElementById('montant').value;
        const numeroClient = document.getElementById('numero').value;
        const agentNum = "0987745033";

        const message = `Bonjour Monsieur Alexis,
Votre client ${nom} souhaite acheter ${choix}.
Nom utilisé : ${nom}
Produit : ${produitSelectionne}
Durée : ${dureeSelectionnee}
Montant : ${montant} FC
Numéro du client : ${numeroClient}`;

        document.getElementById('overlay').style.display = 'flex';

        setTimeout(() => {
            window.location.href = `sms:${agentNum}?body=${encodeURIComponent(message)}`;
        }, 1500);
    }

    function fermerPopup() {
        document.getElementById('overlay').style.display = 'none';
    }
</script>

</body>
</html>

