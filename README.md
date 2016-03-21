# Centreon translation for Centreon web UI #

## Introduction ##

Centreon is one of the most flexible and powerful monitoring softwares
on the market; it is absolutely free and Open Souce (released under GNU
General Public License version 2, see LICENSE file).

This software requires [Centreon Engine](https://github.com/centreon/centreon-engine)
and [Centreon Broker](https://github.com/centreon/centreon-broker) to be
operational.

**Quick links**
* the official [Centreon (company) website](https://www.centreon.com)
* the official [online documentation](https://documentation.centreon.com)
* our [bugtracker](https://github.com/centreon/centreon/issues)
* the [forum](http://forum.centreon.com)
* the [download center](https://download.centreon.com)

## How to participate in the translation of Centreon ##

1. First clone this git project on github:
2. Select your major version of Centreon web:
3. Use existing language directory or create new one

### Create new language directory ###

1. Create your language directory based on only chars. for example 'uk', 'fr' for French, 'es' for Spanish, etc.
2. Create a sub directory 'LC_MESSAGES'
3. Paste message.pot and help.pot from root directory in this one and rename them as message.po and help.po
4. Edit file using a PO editor and start translation
5. Commit your work
6. Send us a pull request

#### Start with existing old translation files ####

You can use an old (Centreon web 2.6 translation in progress). 
1. Checkout files from '2.6' branch
2. Merge this translation with pot files using commands:

  $ msgmerge old_messages.po messages.pot -o <my_dir>/messages.po
  $ msgmerge old_help.po help.pot -o  <my_dir>/help.po 

### Use existing language directory ###

If translation files already exist, just continue to translation missing string:

1. Edit file using a PO editor and start translation
2. Commit your work
3. Send us a pull request

## Use a translation ##

If you want to translate your Centreon Web UI you have to donload translation files and install them:

1. First clone this git repo to your server using command:

  $ git clone https://github.com/centreon/centreon-translations.git

2. And select your major version of Centreon web:

  $ git branch -r
  $ git checkout -b <branch>

3. Create the local directory for Centreon Web UI:

  $ mkdir -p /usr/share/centreon/www/locale/`locale | grep LC_MESSAGES | cut -d \" -f 2`/LC_MESSAGES

Replace '/usr/share/centreon' by installatino dir of your Centreon Web UI.

3. Compile and install your language files:

  $ msgfmt message.po -o /usr/share/centreon/www/locale/`locale | grep LC_MESSAGES | cut -d \" -f 2`/LC_MESSAGES/message.mo

  $ msgfmt help.po -o /usr/share/centreon/www/locale/`locale | grep LC_MESSAGES | cut -d \" -f 2`/LC_MESSAGES/help.mo

4. Restart Apache:

  $ service httpd restart

5. Edit your profil on Centreon Web UI and select language.
