# flask-portfoliofrom flask import Flask, render_template, request

app = Flask(__name__)

@app.route("/")
def home():
    name = "Your Name"
    skills = ["Python", "Flask", "HTML", "CSS"]
    return render_template("index.html", name=name, skills=skills)

@app.route("/contact", methods=["GET", "POST"])
def contact():
    if request.method == "POST":
        username = request.form.get("username")
        email = request.form.get("email")
        message = request.form.get("message")
        return f"Thanks {username}, your message has been received!"
    return render_template("contact.html")

if __name__ == "__main__":
    app.run(debug=True)
