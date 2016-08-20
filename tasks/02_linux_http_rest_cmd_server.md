# Python Task 02

## Helpful information

Study following links:
 - http://farazdagi.com/blog/2014/rest-long-running-jobs/
 - https://docs.python.org/2.7/library/threading.html
 - https://docs.python.org/2/library/basehttpserver.html
 - https://docs.python.org/2/library/socketserver.html
 - http://www.restapitutorial.com/lessons/restfulresourcenaming.html
 - http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
 - https://www.adayinthelifeof.nl/2011/06/02/asynchronous-operations-in-rest/

Useful tools:
 - https://github.com/jkbrzt/httpie


## Subtask 1

Create HTTP REST service witch asynchronously executes shell commands
on host. Please, find more details bellow.

Here are some important requirements:
 - Uses only python standard library.
 - Returns appropriate HTTP codes for responses.
 - At the same time can be executed a few commands.
 - Utilizes recommended practices for creating REST services.
 - Pay attention on HTTP headers and encoding (respects Cyrillic alphabet).

### Service API endpoints examples

#### Working with jobs

 - `http://localhost:8000/api/jobs`

| HTTP Method | Action                       |
|-------------|:-----------------------------|
| GET         | Gets list of existing jobs.  |
| POST        | Creates new job for command. |

 - `http://localhost:8000/api/jobs/12`

| HTTP Method | Action                            |
|-------------|:----------------------------------|
| GET         | Gets url for checking job status. |
| DELETE*     | Removes job from the history.     |

#### Working with jobs statuses

 - `http://localhost:8000/api/statuses`

| HTTP Method | Action                           |
|-------------|:---------------------------------|
| GET         | Gets execution statuses of jobs. |

 - `http://localhost:8000/api/statuses/12`

| HTTP Method | Action                                  |
|-------------|:----------------------------------------|
| GET         | Gets execution status of requested job. |

#### Working with jobs results

 - `http://localhost:8000/api/results`

| HTTP Method | Action                               |
|-------------|:-------------------------------------|
| GET         | Gets list of completed job results.  |

- `http://localhost:8000/api/results/33`

| HTTP Method | Action                                              |
|-------------|:----------------------------------------------------|
| GET         | Gets job result provided after completion of a job. |
| DELETE*     | Removes result from the history.                    |

*Note: all `DELETE` methods are optional and can be skipped.*

### Usage examples

Let me inform you, that all examples bellow might not contain all required
headers. Moreover, JSON outputs provided as examples and can be enhanced.

Ok, let's retrieve a list of submitted jobs:

```bash
$ curl -i http://localhost:8000/api/jobs`
```

JSON output should look like:

```json
{
  "jobs": [
    {
      "job_id": 1,
      "command": "ifconfig",
      "created: "2016-08-09T18:31:42.201"
    },
    {
      "job_id": 33,
      "command": "ls -lah /etc"
      "created": "2016-08-19T15:31:42.201"
    }
  ]
}
```

To create new job execute next command:

```bash
$ curl -X POST -H 'Content-Type: application/json' \
    -d '{"command": "cp  /tmp/file /mnt/nfs/"}' http://localhost:8000/api/jobs
HTTP/1.0 202 Accepted
Location: /api/statuses/45
```

Than check job status using link in `Location` header from previous step:

```bash
$ curl -X GET http://localhost:8000/api/statuses/45
HTTP/1.0 200 Ok
```

JSON output might look like:

```json
{
  "status_id": 45,
  "done": false
}
```

Second attempt might return link witch pointing to our job result.

```bash
$ curl -X GET http://localhost:8000/api/statuses/45
HTTP/1.1 303 See Other
Location: /api/results/4
```

And now we can *finally* get execution result of our command:

```bash
$ curl -X GET http://localhost:8000/api/results/4
HTTP/1.0 200 Ok
```

JSON output might look like:

```json
{
  "result_id": 4,
  "duration": 0.3345,
  "competed": "2016-08-19T15:31:42.201",
  "stdout": "",
  "stderr": "cp: cannot stat ‘/tmp/file’: No such file or directory",
  "exit_code": 1
}
```

*Note: it is better to use `http` command for debug purposes.*


## Subtask 2*

Optional.

TODO:
 - Add add ability to specify queries such as sort, search, etc.
 - Removing tasks sequentially removes job result and status.
 - Authentication via token.
 - Etc.
