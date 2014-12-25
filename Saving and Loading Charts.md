Charting Library supports saving/loading charts on 2 levels of abstraction:

1. **Low-Level**: save/load functionality is present by widget's `save()` and `load()` [[methods|Widget-Methods#savecallback]]. One who uses them should take care of physical storage on his own. But you can save those JSONs where you want to --  in example, you may embed them to your saved pages or user's working area and so on.

2. **High-Level**: Charting Library is able to save or load charts from storage you'll point to. We created a tiny storage sample with Python and PostgreSQL and put it on [our GitHub](https://github.com/tradingview/saveload_backend). You may grab it and run on your own server so you'll have control over all your users' saved data.

#Using High-Level Save/Load

Here are a few steps for those who want to have their own charts storage:

1. Clone our repo to your host
2. Run the data service or use our demo service.Here are a short todo list for those who's not familiar with Django.
  1. Install Python 3.x and Pip.
  2. Install PostgreSQL or some other Django-friendly database engine.
  3. go to you charts storage folder and run `pip install -r requirements.txt`
  4. go to charting_library_charts folder and set up your database connection in settings.py (see `DATABASES` @ line #12). Please remember to create appropriate database in your PostgreSQL.
  5. run `python manage.py migrate` . This will create database schema without any data.
  6. run `python manage.py runserver` to run TEST instance of your database. don't use the command above on production environment. Use some other stuff (i.e., Gunicorn)
3. Set up your Charting Library page: set `charts_storage_url = url-of-your-charts-storage`, also set `client_id` and `user_id` (see details below) in widget's .ctor.
4. Enjoy !

**Remark**: Manual filling/editing database is not the desired usage for this stuff. Please avoid this because you may hurt Django.

#Using Demo Charts Storage

We're running demo charts storage service to let you try save/load as fast as you've got new Library's build. This storage URL is <http://saveload.tradingview.com>. It's just a demo so it is provided as-is. We do not guarantee its stability. Also, we drop all the data from this storage now and again.

#Managing Saved Charts Access
You should take care of which charts your users will be able to see and load. Basically, user can see/load charts having the same `client_id` and `user_id` the user has. `client_id` is an identifier of user's group. It is intended to cover the case when you have few groups of users (i.e, when you have few sites) using the same charts storage. So the common practice is to set `client_id = your-site's-URL`. It's up to you however.

`user_id` is expected to be user's id in context of your `client_id` group. You can either set is to each user individually (to make each user to have his own private charts storage) or set it the same for all users or any users group to create a kind of public storage. Here are a few examples:

client_id|user_id|Effect
---|---|---
your site url or anything else|unique user id|Each user has his private charts storage other users can't see.
your site url or anything else|the same value for all users|Each user can see and load each of saved charts.
your site url or anything else|unique user id for registered users and some constant for all who's anonymous|Each registered user has his private charts storage other users can't see. All anonymous users have one shared storage.
