dict2xml
========

Super Simple utility to convert a python dictionary into an xml string

Installation
------------

Make youself a virtualenv and do the following::

  $ pip install .

Or if you want to develop on dict2xml, recommended commands are::

  $ pip install -e .
  $ pip install -e ".[tests]"

Or if you don't want to install from source::

  $ pip install dict2xml

example
-------

.. code-block:: python

  from dict2xml import dict2xml

  data = {
    'a': 1,
    'b': [2, 3],
    'c': {
      'd': [
        {'p': 9},
        {'o': 10}
      ],
      'e': 7
    }
  }

  print dict2xml(data, wrap="all", indent="  ")

Output
------

.. code-block:: xml

  <all>
    <a>1</a>
    <b>2</b>
    <b>3</b>
    <c>
      <d>
        <p>9</p>
      </d>
      <d>
        <o>10</o>
      </d>
      <e>7</e>
    </c>
  </all>

methods
-------

``dict2xml.dict2xml(data, *args, **kwargs)``
    Equivalent to:

    .. code-block:: python

        dict2xml.Converter(*args, **kwargs).build(data)

``dict2xml.Converter(wrap="", indent="  ", newlines=True)``
    Knows how to convert a dictionary into an xml string

    * wrap: Wraps the entire tree in this tag
    * indent: Amount to prefix each line for each level of nesting
    * newlines: Whether or not to use newlines

``dict2xml.Converter.build(data)``
    Instance method on Converter that takes in the data and creates the xml string

Limitations
-----------

* No attributes on elements
* Currently no explicit way to hook into how to cope with your custom data
* Currently no way to insert an xml declaration line

Changelog
---------

1.7.0 - 16 April, 2020
    * Use collections.abc to avoid deprecation warning. Thanks @mangin.
    * This library no longer supports Python2 and is only supported for
      Python3.6+. Note that the library should still work in Python3.5 as I
      have not used f-strings, but the framework I use for the tests is only 3.6+.

1.6.1 - August 27, 2019
    * Include readme and LICENSE in the package

1.6 - April 27, 2018
    * No code changes
    * changed the licence to MIT
    * Added more metadata to pypi
    * Enabled travis ci
    * Updated the tests slightly

1.5
    * No changelog was kept before this point.
