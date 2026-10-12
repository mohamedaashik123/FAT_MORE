from flask import Flask, request, redirect, session, render_template_string

app = Flask(__name__)
app.secret_key = "fatmore_app_secret_123"

foods = [
    # BREAKFAST
    {"id": 1, "name": "Idli & Sambar", "category": "Breakfast", "price": 40, "emoji": "🍛"},
    {"id": 2, "name": "Masala Dosa", "category": "Breakfast", "price": 70, "emoji": "🥞"},
    {"id": 3, "name": "Pongal", "category": "Breakfast", "price": 50, "emoji": "🍚"},
    {"id": 4, "name": "Poori Masala", "category": "Breakfast", "price": 60, "emoji": "🫓"},
    {"id": 5, "name": "Onion Dosa", "category": "Breakfast", "price": 80, "emoji": "🥞"},
    {"id": 6, "name": "Puttu", "category": "Breakfast", "price": 50, "emoji": "🍚"},
    {"id": 7, "name": "Idiyappam", "category": "Breakfast", "price": 55, "emoji": "🍜"},
    {"id": 8, "name": "Veg Sandwich", "category": "Breakfast", "price": 70, "emoji": "🥪"},

    # LUNCH
    {"id": 9, "name": "Veg Meals", "category": "Lunch", "price": 120, "emoji": "🍱"},
    {"id": 10, "name": "Chicken Biryani", "category": "Lunch", "price": 180, "emoji": "🍗"},
    {"id": 11, "name": "Mutton Biryani", "category": "Lunch", "price": 250, "emoji": "🍖"},
    {"id": 12, "name": "Egg Biryani", "category": "Lunch", "price": 130, "emoji": "🍛"},
    {"id": 13, "name": "Veg Fried Rice", "category": "Lunch", "price": 100, "emoji": "🍚"},
    {"id": 14, "name": "Chicken Fried Rice", "category": "Lunch", "price": 140, "emoji": "🍗"},
    {"id": 15, "name": "Curd Rice", "category": "Lunch", "price": 60, "emoji": "🥣"},
    {"id": 16, "name": "Lemon Rice", "category": "Lunch", "price": 70, "emoji": "🍋"},
    {"id": 17, "name": "Sambar Rice", "category": "Lunch", "price": 70, "emoji": "🍲"},
    {"id": 18, "name": "Paneer Rice", "category": "Lunch", "price": 130, "emoji": "🍚"},

    # DINNER
    {"id": 19, "name": "Parotta", "category": "Dinner", "price": 60, "emoji": "🫓"},
    {"id": 20, "name": "Chapati", "category": "Dinner", "price": 50, "emoji": "🫓"},
    {"id": 21, "name": "Chicken Noodles", "category": "Dinner", "price": 140, "emoji": "🍜"},
    {"id": 22, "name": "Veg Noodles", "category": "Dinner", "price": 100, "emoji": "🍜"},
    {"id": 23, "name": "Pizza", "category": "Dinner", "price": 200, "emoji": "🍕"},
    {"id": 24, "name": "Cheese Burger", "category": "Dinner", "price": 150, "emoji": "🍔"},
    {"id": 25, "name": "Chicken Burger", "category": "Dinner", "price": 170, "emoji": "🍔"},
    {"id": 26, "name": "Paneer Wrap", "category": "Dinner", "price": 110, "emoji": "🌯"},
    {"id": 27, "name": "Chicken Shawarma", "category": "Dinner", "price": 130, "emoji": "🌯"},
    {"id": 28, "name": "White Sauce Pasta", "category": "Dinner", "price": 160, "emoji": "🍝"},

    # SNACKS
    {"id": 29, "name": "French Fries", "category": "Snacks", "price": 80, "emoji": "🍟"},
    {"id": 30, "name": "Samosa", "category": "Snacks", "price": 20, "emoji": "🥟"},
    {"id": 31, "name": "Veg Puff", "category": "Snacks", "price": 25, "emoji": "🥐"},
    {"id": 32, "name": "Chicken Nuggets", "category": "Snacks", "price": 100, "emoji": "🍗"},
    {"id": 33, "name": "Garlic Bread", "category": "Snacks", "price": 90, "emoji": "🥖"},
    {"id": 34, "name": "Spring Roll", "category": "Snacks", "price": 80, "emoji": "🌯"},
    {"id": 35, "name": "Popcorn", "category": "Snacks", "price": 50, "emoji": "🍿"},
    {"id": 36, "name": "Veg Momos", "category": "Snacks", "price": 80, "emoji": "🥟"},

    # DRINKS
    {"id": 37, "name": "Fresh Orange Juice", "category": "Drinks", "price": 60, "emoji": "🍊"},
    {"id": 38, "name": "Cold Coffee", "category": "Drinks", "price": 80, "emoji": "🥤"},
    {"id": 39, "name": "Lemon Juice", "category": "Drinks", "price": 30, "emoji": "🍋"},
    {"id": 40, "name": "Chocolate Milkshake", "category": "Drinks", "price": 100, "emoji": "🥛"},
    {"id": 41, "name": "Strawberry Milkshake", "category": "Drinks", "price": 100, "emoji": "🍓"},
    {"id": 42, "name": "Iced Tea", "category": "Drinks", "price": 60, "emoji": "🧋"},

    # DESSERTS
    {"id": 43, "name": "Chocolate Brownie", "category": "Desserts", "price": 90, "emoji": "🍫"},
    {"id": 44, "name": "Ice Cream", "category": "Desserts", "price": 70, "emoji": "🍨"},
    {"id": 45, "name": "Gulab Jamun", "category": "Desserts", "price": 50, "emoji": "🍮"},
    {"id": 46, "name": "Chocolate Cake", "category": "Desserts", "price": 100, "emoji": "🍰"},
    {"id": 47, "name": "Fruit Salad", "category": "Desserts", "price": 80, "emoji": "🍓"},
    {"id": 48, "name": "Falooda", "category": "Desserts", "price": 110, "emoji": "🍧"}
]

STYLE = """
<style>
* { box-sizing: border-box; }
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #fff8f0;
    color: #29251f;
}
header {
    background: #e95420;
    color: white;
    text-align: center;
    padding: 20px;
}
nav {
    background: white;
    padding: 16px;
    text-align: center;
    box-shadow: 0 2px 6px #ddd;
}
nav a {
    display: inline-block;
    margin: 7px;
    text-decoration: none;
    color: #d94b1d;
    font-weight: bold;
}
.container {
    max-width: 950px;
    margin: 25px auto;
    padding: 15px;
}
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
    gap: 16px;
}
.card {
    background: white;
    padding: 20px;
    border-radius: 13px;
    box-shadow: 0 3px 12px #eadfd4;
}
.food-emoji { font-size: 40px; }
button, .button {
    display: inline-block;
    background: #f05a28;
    color: white;
    border: none;
    padding: 11px 16px;
    border-radius: 7px;
    cursor: pointer;
    text-decoration: none;
    margin-top: 8px;
}
input {
    width: 100%;
    padding: 13px;
    margin: 8px 0;
    border: 1px solid #ddd;
    border-radius: 7px;
}
.price { color: #e95420; font-weight: bold; }
.center { text-align: center; }
.heart { color: #e95420; }
.hero {
    background: #29251f;
    color: white;
    padding: 30px;
    border-radius: 15px;
    margin-bottom: 25px;
}
.small { color: #777; }
</style>
"""

def page(content, title="Fatmore"):
    return render_template_string("""
    <!DOCTYPE html>
    <html>
    <head>
        <title>{{ title }}</title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        {{ style|safe }}
    </head>
    <body>
        <header>
            <h1>🍽️ Fatmore</h1>
            <p>Good Food. Good Mood.</p>
        </header>
        {% if logged %}
        <nav>
            <a href="/home">🏠 Home</a>
            <a href="/home?category=Breakfast">🍳 Breakfast</a>
            <a href="/home?category=Lunch">🍱 Lunch</a>
            <a href="/home?category=Dinner">🍕 Dinner</a>
            <a href="/home?category=Snacks">🍟 Snacks</a>
            <a href="/favorites">❤️ Favorites</a>
            <a href="/cart">🛒 Cart ({{ count }})</a>
            <a href="/logout">Logout</a>
        </nav>
        {% endif %}
        {{ content|safe }}
    </body>
    </html>
    """, content=content, title=title, style=STYLE,
       logged=("user" in session),
       count=len(session.get("cart", [])))


@app.route("/")
def login():
    if "user" in session:
        return redirect("/home")

    return page("""
    <div class="container">
      <div class="card center">
        <div class="food-emoji">🍔</div>
        <h2>Welcome to Fatmore!</h2>
        <p>Fresh food delivered to your door.</p>
        <form method="POST" action="/login">
          <input name="username" placeholder="Username" required>
          <input name="password" type="password"
                 placeholder="Password" required>
          <button type="submit">Login</button>
        </form>
        <p class="small">Demo username: student</p>
        <p class="small">Demo password: 1234</p>
      </div>
    </div>
    """)


@app.route("/login", methods=["POST"])
def do_login():
    username = request.form.get("username", "").strip()
    password = request.form.get("password", "")

    if username == "student" and password == "1234":
        session["user"] = username
        session["cart"] = []
        session["favorites"] = []
        return redirect("/home")

    return page("""
    <div class="container card center">
      <h2>Incorrect login details</h2>
      <a class="button" href="/">Try Again</a>
    </div>
    """)


@app.route("/home")
def home():
    if "user" not in session:
        return redirect("/")

    category = request.args.get("category", "All")
    search = request.args.get("search", "").strip().lower()

    selected = [
        f for f in foods
        if (category == "All" or f["category"] == category)
        and search in f["name"].lower()
    ]

    cards = ""

    for f in selected:
        fav = "❤️" if f["id"] in session.get("favorites", []) else "🤍"
        cards += f"""
        <div class="card center">
          <div class="food-emoji">{f['emoji']}</div>
          <h3>{f['name']}</h3>
          <p class="small">{f['category']}</p>
          <p class="price">₹{f['price']}</p>

          <form method="POST" action="/add/{f['id']}">
            <button>Add to Cart 🛒</button>
          </form>

          <form method="POST" action="/favorite/{f['id']}">
            <button>{fav} Favourite</button>
          </form>
        </div>
        """

    if not cards:
        cards = "<div class='card'>No food found. Try another search.</div>"

    return page(f"""
    <div class="container">
      <div class="hero">
        <h2>Hello, {session['user']}! 👋</h2>
        <h2>Good Food, Good Mood!</h2>
        <p>Find your favourite food in seconds.</p>
      </div>

      <form method="GET" action="/home">
        <input name="search" placeholder="🔍 Search your food..."
               value="{search}">
        <button>Search Food</button>
      </form>

      <h2>Explore Categories</h2>
      <div class="grid">
        <a class="button" href="/home?category=Breakfast">🌅 Breakfast</a>
        <a class="button" href="/home?category=Lunch">🍱 Lunch</a>
        <a class="button" href="/home?category=Dinner">🌙 Dinner</a>
        <a class="button" href="/home?category=Snacks">🍟 Snacks</a>
        <a class="button" href="/home?category=Drinks">🥤 Drinks</a>
        <a class="button" href="/home">All Foods</a>
      </div>

      <h2>🍽️ Our Menu</h2>
      <div class="grid">{cards}</div>
    </div>
    """)


@app.route("/add/<int:food_id>", methods=["POST"])
def add(food_id):
    if "user" not in session:
        return redirect("/")

    if any(f["id"] == food_id for f in foods):
        cart = session.get("cart", [])
        cart.append(food_id)
        session["cart"] = cart

    return redirect("/cart")


@app.route("/favorite/<int:food_id>", methods=["POST"])
def favorite(food_id):
    if "user" not in session:
        return redirect("/")

    favs = session.get("favorites", [])

    if food_id in favs:
        favs.remove(food_id)
    elif any(f["id"] == food_id for f in foods):
        favs.append(food_id)

    session["favorites"] = favs
    return redirect("/home")


@app.route("/favorites")
def favorites():
    if "user" not in session:
        return redirect("/")

    favs = session.get("favorites", [])
    cards = ""

    for f in foods:
        if f["id"] in favs:
            cards += f"""
            <div class="card center">
              <div class="food-emoji">{f['emoji']}</div>
              <h3>{f['name']} ❤️</h3>
              <p class="price">₹{f['price']}</p>
              <form method="POST" action="/add/{f['id']}">
                <button>Add to Cart</button>
              </form>
            </div>
            """

    if not cards:
        cards = "<div class='card'>No favorites yet. Choose a food and tap Favourite.</div>"

    return page(f"""
    <div class="container">
      <h2>❤️ My Favourite Foods</h2>
      <div class="grid">{cards}</div>
    </div>
    """)


@app.route("/cart")
def cart():
    if "user" not in session:
        return redirect("/")

    cart_ids = session.get("cart", [])
    items = [f for f in foods if f["id"] in cart_ids]
    total = sum(f["price"] for f in items)

    cards = ""

    for f in items:
        cards += f"""
        <div class="card">
          {f['emoji']} <b>{f['name']}</b>
          <span class="price"> — ₹{f['price']}</span>
          <form method="POST" action="/remove/{f['id']}">
            <button>Remove</button>
          </form>
        </div>
        """

    if not cards:
        cards = "<div class='card'>Your cart is empty. Add some delicious food!</div>"

    checkout = ""
    if items:
        checkout = f"""
        <div class="card">
          <h2>Total Bill: ₹{total}</h2>
          <form method="POST" action="/order">
            <button>Place Order ✅</button>
          </form>
        </div>
        """

    return page(f"""
    <div class="container">
      <h2>🛒 My Shopping Cart</h2>
      {cards}
      {checkout}
      <a class="button" href="/home">Continue Shopping</a>
    </div>
    """)


@app.route("/remove/<int:food_id>", methods=["POST"])
def remove(food_id):
    cart_ids = session.get("cart", [])

    if food_id in cart_ids:
        cart_ids.remove(food_id)

    session["cart"] = cart_ids
    return redirect("/cart")


@app.route("/order", methods=["POST"])
def order():
    if "user" not in session:
        return redirect("/")

    cart_ids = session.get("cart", [])
    items = [f for f in foods if f["id"] in cart_ids]
    total = sum(f["price"] for f in items)

    if not items:
        return redirect("/cart")

    session["cart"] = []

    return page(f"""
    <div class="container card center">
      <div class="food-emoji">✅</div>
      <h2>Order Placed Successfully!</h2>
      <p>Thank you for choosing Foodie.</p>
      <h2>Total: ₹{total}</h2>
      <a class="button" href="/home">Back to Home</a>
    </div>
    """)


@app.route("/logout")
def logout():
    session.clear()
    return redirect("/")


if __name__ == "__main__":
    app.run(debug=False, port=5001)
