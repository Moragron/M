# Importing
from flask import Flask, request, render_template, redirect, session
from flask_session import Session


app = Flask(__name__)       # Setting up our application - (__name__ is referencing this file)
app.config["SESSION_PERMANENT"] = False
app.config["SESSION_TYPE"] = "filesystem"
Session(app)


# -------------------------------------------------------------
# Note the definition of two different and optional methods in case of a form:
# When we receive an HTTP POST request -
# we get the parameters from the post request, and
# display it in the result HTML - show_week_plan.html
# The post method will be called when someone clicks
# submit button (send) in the get_inputs.html form

# -------------------------------------------------------------

@app.route('/', methods= ['POST', 'GET'])
# Defining the view function to homepage route:
def view_func():
    # If the user clicked on the "submit" button:
    if request.method == 'POST':
        email = request.form['email']
        return render_template("homepage.html", email=email)
    else:
        return render_template("Login.html")

@app.route("/Subregister", methods=['POST', 'GET'])
def Subregister():
    if request.method == 'POST':
        return render_template("Login.html")
    else:
        return render_template("Subregister.html")


# Running the script
if __name__ == "__main__":
    app.run(port="3000")
