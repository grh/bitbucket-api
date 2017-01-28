```
NAME
    bitbucket-api - command-line utility to interact with Bitbucket

SYNOPSIS 
    bitbucket-api -u username [command] [options] 

DESCRIPTION
    bitbucket-api is a Bash command-line Ruby script which can be used to
    create, modify, and delete repositories hosted on bitbucket.org. It
    does so by parsing the options given and making an HTTP request to
    the Bitbucket API. It requires ruby and curl to function properly.

COMMANDS
    -u username     Bitbucket username

    --create-project teamname projectkey [options]      Create a project

            teamname and projectkey are the lowercase string identifiers
            used by Bitbucket. For the options available, see --options.

            Currently, you can only create an empty project and then
            create new repositories associated with that project. There
            is no API facility yet to associate existing repositories to
            a new project.

            NOTE: the Bitbucket API follows REST API conventions. That
            is, it utilizes the HTTP request methods (GET, POST, PUT,
            DELETE) to determine the type of action to perform.
            Therefore, you cannot use the create option in conjunction
            with the delete or update options. Those options must be
            utilized in separate utility calls.

    --delete-project teamname projectkey        Delete a project

            teamname and projectkey are the lowercase string identifiers
            used by Bitbucket. For the options available, see --options.

            NOTE: the Bitbucket API follows REST API conventions. That
            is, it utilizes the HTTP request methods (GET, POST, PUT,
            DELETE) to determine the type of action to perform.
            Therefore, you cannot use the delete option in conjunction
            with the create or update options. Those options must be
            utilized in separate utility calls.

    --update-project teamname projectkey [options]      Update a project

            teamname and projectkey are the lowercase string identifiers
            used by Bitbucket. For the options available, see --options.

            Currently, there is no API facility to associate existing
            repositories to an existing project.

            NOTE: the Bitbucket API follows REST API conventions. That
            is, it utilizes the HTTP request methods (GET, POST, PUT,
            DELETE) to determine the type of action to perform.
            Therefore, you cannot use the update option in conjunction
            with the create or delete options. Those options must be
            utilized in separate utility calls.

    --create-repository reponame [options]      Create a repository

            reponame is the lowercase repository string identifier
            used by Bitbucket (also known as the repo-slug). For the
            options available, see --options.

            NOTE: the Bitbucket API follows REST API conventions. That
            is, it utilizes the HTTP request methods (GET, POST, PUT,
            DELETE) to determine the type of action to perform.
            Therefore, you cannot use the create option in conjunction
            with the delete or update options. Those options must be
            utilized in separate utility calls.

    --delete-repository reponame        Delete a repository

            reponame is the lowercase repository string identifier
            used by Bitbucket (also known as the repo-slug).

            NOTE: the Bitbucket API follows REST API conventions. That
            is, it utilizes the HTTP request methods (GET, POST, PUT,
            DELETE) to determine the type of action to perform.
            Therefore, you cannot use the delete option in conjunction
            with the create or update options. Those options must be
            utilized in separate utility calls.

    --update-repository reponame [options]      Update a repository

            reponame is the lowercase repository string identifier
            used by Bitbucket (also known as the repo-slug). For the
            options available, see --options.

            NOTE: the Bitbucket API follows REST API conventions. That
            is, it utilizes the HTTP request methods (GET, POST, PUT,
            DELETE) to determine the type of action to perform.
            Therefore, you cannot use the update option in conjunction
            with the create or delete options. Those options must be
            utilized in separate utility calls.

    --set-group-privileges teamname groupname=value

            Set repository privileges for a team group.

            teamname and groupname are the lowercase string identifiers
            used by Bitbucket. value is one of read, write, admin, or
            delete.

    --set-user-privileges reponame acctname=value

            Set repository privileges for a single user.

            reponame and acctname are the lowercase string identifiers
            used by Bitbucket. value is one of read, write, admin, or
            delete.

OPTIONS
    --options name=value,name=value,...         Set command options

            The options list is a comma-separated series of name=value
            pairs. Available options include:

            fork_policy             allow_forks, no_public_forks, 
                                            or no_forks

            is_private              true or false

            projectkey              project key

            projectname             project name

            reponame                lowercase repository identifer

            team                    lowercase team identifier

EXAMPLES

    Create a private repository named myRepo in project proj1 belonging
    to team team1

        bitbucket-api -u username --create-repository myRepo \
            --options is_private=true,team=team1,projectkey=proj1

    Delete the myRepo repository:

        bitbucket-api -u username --delete-repository myRepo

    Remove group1 privileges from myRepo for team1:

        bitbucket-api -u username --set-group-privileges team1 \
            group1:delete

    Give user1 write privileges on myRepo:

        bitbucket-api -u username --set-repository-privileges myRepo \
            user1:write

TO DO

    - Add additional API endpoints/parameters as command/options
    - Fix --create-project: --options is_private="true" gives expected
      boolean error

LICENSE

    Copyright (c) 2017 Guymon Hall

    Permission is hereby granted, free of charge, to any person
    obtaining a copy of this software and associated documentation files
    (the "Software"), to deal in the Software without restriction,
    including without limitation the rights to use, copy, modify, merge,
    publish, distribute, sublicense, and/or sell copies of the Software,
    and to permit persons to whom the Software is furnished to do so,
    subject to the following conditions:

    The above copyright notice and this permission notice shall be
    included in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
    EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
    MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
    NONINFRINGEMENT.  IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS
    BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN
    ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
    CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
```
