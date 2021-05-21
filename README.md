Django REST API User registration

To run the Virtual environment use:

pipenv shell

To install requirements run:

pip install -r requirements.txt

To run the server use: 

python manage.py runserver

To run migrations use:

python manage.py makemigrations
python manage.py migrate


To create a Super User:

python manage.py createsuperuser

and follow the prompted steps.



USER Registration usage:

To register an user:


POST http://127.0.0.1:8000/api/register/

{
    "username": "admin",
    "email": "admin@bot.com",
    "password": "Password@123"
}

Should return something like this:

{
    "user": {
        "id": 1,
        "username": "admin",
        "email": "admin@bot.com"
    },
    "token": "fa7c63bc04b3d9e55624867177b37071ccb1d62fc729891485edad7250b925b1"
}

To Login an existing user:

POST http://127.0.0.1:8000/api/login/

{
    "username": "admin",
    "password": "Password@123"
}


If the user exist and the credentials are valid, it should return:

{
    "expiry": "2021-05-22T02:01:12.786482Z",
    "token": "f684bab07bad0419fbcb3bdd355e402193a72af6c2b2808f8d1d812e19d91266"
}

If the credetials arent correct it will return:

{
    "non_field_errors": [
        "Unable to log in with provided credentials."
    ]
}

To logout and user:

POST http://127.0.0.1:8000/api/logout/

And in the header include:

Key: Authorization
Value: Token f684bab07bad0419fbcb3bdd355e402193a72af6c2b2808f8d1d812e19d91266

It would not return any content. 