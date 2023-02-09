=========
spade_rpc
=========


.. image:: https://img.shields.io/pypi/v/spade_rpc.svg
        :target: https://pypi.python.org/pypi/spade_rpc

.. image:: https://img.shields.io/travis/NikoConn/spade_rpc.svg
        :target: https://travis-ci.com/NikoConn/spade_rpc

.. image:: https://readthedocs.org/projects/spade-rpc/badge/?version=latest
        :target: https://spade-rpc.readthedocs.io/en/latest/?version=latest
        :alt: Documentation Status




Plugin for SPADE platform to implement rpc protocol on agents


* Free software: MIT license
* Documentation: https://spade-rpc.readthedocs.io. (TODO)


Features
--------

* Create agents that can use the Jabber RPC protocol
* Call methods on remote agents
* Register/unregister methods on agents

Examples
--------

Calling a method:

::

    from spade_rpc import RPCAgent

    rpc_client = RPCAgent(client_jid)
    result = rpc_client.rpc.call_method(server_jid, 'sum', [1, 2])
    print(result)

::

Registering a method:

::

    from spade_rpc import RPCAgent

    def sum(a, b):
            return a + b

    rpc_server = RPCAgent(server_jid)
    rpc_server.rpc.register_method(sum, 'sum')

::

A client serving a method can also define a function for selecting if the methdod is allowed to be called

::

    def is_allowed(jid):
            return jid in ['foo', 'bar']

    rpc_server = RPCAgent(server_jid)
    rpc_server.rpc.register_method(sum, 'sum', is_allowed)

::

More complete examples can be found in the `examples folder <examples>`_

Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage
