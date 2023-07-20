# Redis

# Resources

 * [redis.io] [documentation](https://redis.io/docs/), [getting started] (https://redis.io/docs/getting-started/)
 * [python mdoule](https://redis.readthedocs.io/en/stable/)
 * Real Python [How to use with Python](https://realpython.com/python-redis/#first-steps) tutorial.


# Commands

List all keys

    redis-cli keys *

Lists keys (numbered).  The following lists just the keys:

    redis-cli --scan --pattern '*'

Operations on keys can be made by piping the list to xargs redis-cli, such as

    redis-cli --scan --pattern 'ishl7*' | xargs -0 redis-cli del

-0 may help when there are spaces in the keys.  See [man xargs](https://www.man7.org/linux/man-pages/man1/xargs.1.html)

# In a container

See the official container [documentation](https://hub.docker.com/_/redis/)

 * Run with persistant storage
 * set log level
 * 