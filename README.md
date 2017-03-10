# ras-largeProject-Example

This is a simple project example of how a large Flask application can/should be layed out. In other words if you think
your microservice has distinct areas of concern or you find your app.py becomes larger than 750 lines of code you may
want to use this example of how to lay your application out.

## How should I run?

After doing the pip install stuff you can run with:

	/> python run.py
	

## Why is my start point 'empty' of typical code!

Pay particular attention to how the run.py only has the use of the 'run' method to run the application. It's void of
the typical config boiler plate code that many example tutorials have on the internet. That's because they are examples
made to demonstrate how quick the system is to get up and running.

## What is the 'kilt' app??

Also notice that the app name is 'kilt' and not 'app' that many examples have. This often causes confusion in many
developers as the python application file is often called 'app.py'. I'm Scottish and thought 'kilt' is a strange enough
name to make it stick out in your head! Mmaking it clear to everyone that:
1) run.py is what it says, it's your start point to run your application nothing more and nothing else should be in it.
2) the app name is 'kilt' and that's what all your import names use and what the refer to, so no more confussion with
circular imports!

## There is a whole directory with model view controller in /mod_auth, what is going on!

This controls login for the application. And we use 'blueprints' to control this. In the init.py you will notice
how we import from the 'app' directory - as that is how python looks at a module and use that import to register our
'blueprint'.

This allows our 'blueprint' of the mod_auth to add the blueprint:

	/> mod_auth = Blueprint('auth', __name__, url_prefix='/auth')

It then allows us to add routes to a base route in our decorators like this:

	/> @mod_auth.route('/signin/', methods=['GET', 'POST'])


## Where is all our DB code and config code?

Yip, exactly. It's in our __init__.py file. It makes all the config type stuff happen in the initialisation of the
modules. Have a read at the route __init__.py and the __init__.py in the mod_auth module. It's the way forwared!

:-)

Enjoy....
