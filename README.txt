ucb_envconf-6.x-1.x
===================

PURPOSE
-------

UCB Environment Configurations (ucb_envconf) is a small module that
defines configuration depending on the environment (dev/test/live) of
the site. Basically:

if ($site_env == 'live') {
  variable_set('cas_server', auth.berkeley.edu)
} 
elseif ($site_env == 'dev') OR ($site_env == 'test') {
  variable_set('cas_server', auth-test.berkeley.edu)
}

There are a number of ways this goal might be achieved:

1. Insert conditional logic into settings.php
2. Use a module like this one
3. Write a Rule triggered by cron

We chose #2 because

- Can limit user confusion by doing form_alters explaining about
  hard-coded variables which don't change when admin forms are
  submitted.

- Users can easily disable the module if they don't like the
  functionality.

- Can set $conf['cas_attributes']['ldap']['server'] and still leave
  $conf['cas_attributes']['relationships'] configurable by the site
  admin.

BRANCHES
--------

See the github branches for the actual code.
