```
NAME
    bitbucket-api - command-line utility to interact with Bitbucket

SYNOPSIS 
    bitbucket-api -u username -r reponame [options] 

DESCRIPTION
    bitbucket-api is a Bash command-line Ruby script which can be used to
    create, modify, and delete repositories hosted on bitbucket.org. It
    does so by parsing the options given and making an HTTP request to
    the Bitbucket API. It requires curl to function properly.

OPTIONS
    -u username     Bitbucket username

    -r reponame     Bitbucket repository name

    -c              create a repository

                    NOTE: the Bitbucket API follows REST API
                    conventions. That is, it utilizes the HTTP
                    request methods (GET, POST, PUT, DELETE) to
                    determine the type of action to perform.
                    Therefore, you cannot use the delete option in
                    conjunction with the create option. Those
                    options must be utilized in separate utility
                    calls.

    -d              delete a repository

                    NOTE: the Bitbucket API follows REST API
                    conventions. That is, it utilizes the HTTP
                    request methods (GET, POST, PUT, DELETE) to
                    determine the type of action to perform.
                    Therefore, you cannot use the delete option in
                    conjunction with the create option. Those
                    options must be utilized in separate utility
                    calls.

    --group-privileges groupname=value

                    Set repository privileges for a team group.

                    groupname is the lowercase group string identifier
                    used by Bitbucket, and the value is one of read,
                    write, admin, or delete.

    --options name=value,name=value,...

                    The options list is simple a comma-separated series
                    of name=value pairs. Available options include:

                    private=boolean     true or false

    --privileges username=value

                    Set repository privileges for a single user.

                    username is the lowercase string identifier used by
                    Bitbucket, and the value is one of read, write,
                    admin, or delete.

    --project projectkey 

                    Use this option to specify a particular project to
                    which a repository belongs.

    --team teamname     

                    Use this option to specify the team name to which a
                    repository belongs.

EXAMPLES

    Create a private repository named myRepo for a team named team1:

        bitbucket-api -u username -r myRepo --team team1 \
            --options private=true

    Delete the myRepo repository:

        bitbucket-api -u username -r myRepo -d

    Remove group1 privileges from myRepo for team1:

        bitbucket-api -u username -r myRepo --team team1 \
            --group-privileges group1:delete

    Give user1 write privileges on myRepo:

        bitbucket-api -u username -r myRepo --privileges user1:write

TO DO

    - Add additional API endpoints/parameters as --options

    - Rewrite this in Python (?)

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
