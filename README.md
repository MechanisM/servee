* On Freenode #servee

Servee is a special purpose django-admin for editing content on the front end of your site.

* Docs at [Read The Docs][rtd]

First you should put servee in your environment:

    pip install django-servee
    
We're also keeping a [dist server of our own][1].

[1]: http://dist.servee.com/dev/

or download and

    ./setup.py develop

Then add servee to your installed apps.

At a minimum, you want to install `servee.frontendadmin`.  This is
the admin site.  You probably also want our wysiwyg tools, and the tinymce
backend (only supported wysiwyg editor at the moment) This converts your textareas
to wysiwyg areas, and that's awesome (sometimes).

    INSTALLED_APPS += [
        "servee.frontendadmin",
        "servee.wysiwyg",
        "servee.wysiwyg.tinymce", 
    ]

Then syncdb.  Servee assumes that you're using either contrib.staticfiles or django-staticfiles (>=1.1)
Make sure that you collectstatic in production.

It's important to add servee urls, and you probably want to use autodiscover.
    
    from servee import frontendadmin
    frontendadmin.site.autodiscover()
    # ...
    url(r"^servee/", include(frontendadmin.site.urls)),

At this point, you're really going to want to get into the [docs][rtd].

[rtd]: http://django-servee.readthedocs.org/en/latest/index.html
