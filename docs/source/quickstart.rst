Knowledge-Base Interface quickstart
====================================================
This section describes the necessary steps to initialize and use the Knowledge-Base Interface.

API simple usage
----------------

Imports::

    from Interface_KB import KB_Interface,InterfaceObjects

Initialization::

    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

API usage::

    print(API.getASG.__doc__)

This API call will return the function documentation for the getASG() function.

API usage examples
------------------

For more complex API usage, please see the examples provided in the different example sections:

* :doc:`Core_examples`
* :doc:`ASG_examples`
* :doc:`DFA_examples`
* :doc:`Performance_examples`
* :doc:`ContractOntology_examples`

.. only:: builder_html

    .. important:: :download:`Download <SharedFiles/input.zip>` the input artifacts(KB instances, MM instances,JSON objects,...) needed to run the more complex KB API examples. Simply extract the folder in your work directory to start using the KB API examples.


