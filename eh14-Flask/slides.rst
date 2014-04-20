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


Projektbeispiele
================

Moinmoin 2
----------

* Wiki mit primärem Dateibackend / keine "Datenbank"
* Version 1 hatte alles selbstentwickelt
* Version 2 verwendet bewährte Komponenten
* braucht weitere Entwickler für Version 2
* http://moinmo.in/

Webbib
------

* Weboberfläche für Bibliographie-Daten
* entwickelt an dem Wochenende nachdem Flask von Armin Romnacher vorgestellt wurde im Jahre 2010
* keine "Datenbank" / läd Daten beim ersten Request; ab dann aus dem RAM durch g-object
* https://github.com/mfa/webbib

weight-app
----------

* Tracking des eigenen Gewichts
* Pushen des Gewichts zu fitbit
* Versuch Datenbank/Nutzerverwaltung auch mit Flask zu machen
* würde ich heute in Django schreiben
* https://github.com/mfa/weight-app

einfache Endpoints für Arduino-HTTP-POST
----------------------------------------

::

  @app.route('/input/', methods=['POST', 'GET'])
  def inputx():
    if request.headers.get('X-ApiKey') != 'INSERT RANDOM KEY HERE':
      abort(403)
    if request.method == 'POST':
      log_to_file(request.data)
      log_to_rrd(request.data)
    return "OK"


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
