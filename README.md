# card-exchange
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pokémon Card Trading</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Pokémon Card Trading</h1>
    </header>
    <main>
        <section id="card-list-section">
            <h2>Your Cards</h2>
            <div id="card-list">
                <!-- Cards will be displayed here -->
            </div>
        </section>

        <section id="add-card-section">
            <h2>Add a Pokémon Card</h2>
            <form id="add-card-form">
                <input type="text" id="card-name" placeholder="Card Name" required>
                <input type="text" id="card-number" placeholder="Card Number" required>
                <input type="text" id="card-type" placeholder="Type (e.g. Fire, Water)" required>
                <button type="submit">Add Card</button>
            </form>
        </section>

        <section id="trade-section">
            <h2>Request a Trade</h2>
            <form id="trade-form">
                <input type="text" id="my-card" placeholder="Your Card Name" required>
                <input type="text" id="desired-card" placeholder="Desired Card Name" required>
                <button type="submit">Request Trade</button>
            </form>
            <div id="trade-requests">
                <!-- Trade requests will be shown here -->
            </div>
        </section>
    </main>
    <script>
    // Simple JS for adding cards and trade requests
    const cardList = [];
    const tradeRequests = [];

    const cardListDiv = document.getElementById('card-list');
    const addCardForm = document.getElementById('add-card-form');
    const tradeForm = document.getElementById('trade-form');
    const tradeRequestsDiv = document.getElementById('trade-requests');

    function renderCards() {
        cardListDiv.innerHTML = '';
        cardList.forEach(card => {
            const cardDiv = document.createElement('div');
            cardDiv.className = 'card';
            cardDiv.innerHTML = `<b>${card.name}</b> (#${card.number})<br>Type: ${card.type}`;
            cardListDiv.appendChild(cardDiv);
        });
    }

    addCardForm.onsubmit = function(e) {
        e.preventDefault();
        const name = document.getElementById('card-name').value;
        const number = document.getElementById('card-number').value;
        const type = document.getElementById('card-type').value;
        cardList.push({ name, number, type });
        renderCards();
        addCardForm.reset();
    };

    function renderTradeRequests() {
        tradeRequestsDiv.innerHTML = '';
        tradeRequests.forEach(req => {
            const reqDiv = document.createElement('div');
            reqDiv.className = 'trade-request';
            reqDiv.innerHTML = `${req.myCard} wants to trade for ${req.desiredCard}`;
            tradeRequestsDiv.appendChild(reqDiv);
        });
    }

    tradeForm.onsubmit = function(e) {
        e.preventDefault();
        const myCard = document.getElementById('my-card').value;
        const desiredCard = document.getElementById('desired-card').value;
        tradeRequests.push({ myCard, desiredCard });
        renderTradeRequests();
        tradeForm.reset();
    };
    </script>
</body>
</html>
