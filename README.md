Ansible Role: Postfix
=========

An Ansible role that manages Postfix. Currently the role only installs the
postfix package and manages the service. No other functionality so far.

Requirements
------------

No pre-requisites necessary at the moment.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    postfix_state: started

Set the initial state of the postfix daemon when this role is run. This should
generally remain `started`. There occasions where setting this to `stopped`
might come in handy, i.e. during a maintenance down. In combination with the
`postfix_`

    postfix_enabled: true

This sets the boot time status of the Postfix daemon. Should remain to `true`
unless the daemon shouldn't be automatically started at boot time.

    postfix_restart_state: restarted

This determines the measure that is taken when the `postfix` handlers
called. The default is to restart the Postfix process, when the handlers kicks
in. Can be set to `reloaded` to only reload the Postfix process.

    postfix_packages_state: present

The initial packages state is `present`, which means the default packages are
getting installed if not yet present. If you want to automatically update the
package if newer versions are available, set this to `latest`. In case you want
to disable and remove the service, set this to `absent`.

Dependencies
------------

This role has no dependencies to other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed
in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: unibe_idsys.postifx }

License
-------

MIT

Author Information
------------------

The role was created in 2023 by the IT-Services Office of the University of Bern
