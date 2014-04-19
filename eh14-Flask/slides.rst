Flask
=====

Wenn Django zu groß ist.
------------------------

by Andreas Madsack (`@mfandreas <https://twitter.com/mfandreas>`_)

auf der EasterHegg 2014


Was ist Flask
=============

* Microwebframework
* sehr wenig Code / viel Dokumentation
* erprobte Komponenten: Jinja2, Werkzeug


Was kann Flask
==============

* Sessions (cookie-basiert)
* Jinja2 vorkonfiguriert (mit escaping)
* Statische Dateien
* Routing


Hello World
===========

::

  from flask import Flask 
  app = Flask(__name__)

  @app.route('/') 
  def index():
    return 'Hello  World!'

  if __name__ == '__main__':
    app.run(debug=True)


Kontaktformular
===============

::

  from flask import render_template, request, \
     redirect, url_for

  @app.route('/contact/', methods=['POST', 'GET'])
  def contact():
    if request.method == 'POST':
      mail_contact(request.form)
      return redirect(url_for('contact_done'))
    return render_template('contact.html')


Für was nun Flask verwenden
===========================

Projekte, die

* keine Datenbank brauchen
* eine Nutzerverwaltung/Adminoberfläche einfach nicht brauchen
* stark an den Vorgaben von Django vorbeigehen würde


diverese Anwendungsbeispiele
============================

* Moin2 -- verwendet vieles aus der Flask/Jinja/Werkzeug-Welt
* Disqus -- Kommentarsystem mit echten vielen Nutzern
* Ergebnisprotokollbackend für 1Mio+ Seitenaufrufe/Tag (mit Redis)


Was nun? Flask oder Django
==========================

Pro Django
----------

* Datenbankanbindung (ORM, multi-DB)
* Adminoberfläche (deutlich stabiler als die Nachbauten für SQLAlchemy)
* Userverwaltung (sehr stabil)

Pro Flask
---------

* klein
* simple
* trotzdem unendlich erweiterbar



Fragen?
=======

Votrag: https://github.com/mfa/talks/eh14-Flask/

Links
-----

* http://flask.pocoo.org/
* http://www.djangoproject.com/
