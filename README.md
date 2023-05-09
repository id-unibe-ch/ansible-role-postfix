# Ansible Role: Postfix

An Ansible role that manages Postfix. Currently the role only installs the
postfix package and manages the service. No other functionality so far.

## Requirements

No pre-requisites necessary at the moment.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    postfix_alias_map: undef

This allows manipulations of the `hash:/etc/alises` map. The default is not to edit
this file in any way. Use this to forward local mails to external addresses,
which is useful for mails to the local root account. Examples:

    postfix_alias_map:
      www: "user1@test.com"
      root: ["user2@test.com", "user3@example.com"]

Use the local account you want to forward mails for as the key and either a
string or list of strings for the mail addresses to forward these mails to. In
the above example, mails to root are forwarded to two external addresses instead.

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

## Dependencies

This role has no dependencies to other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: unibe_idsys.postifx }

## License

MIT

## Author Information

The role was created in 2023 by the IT-Services Office of the University of Bern
