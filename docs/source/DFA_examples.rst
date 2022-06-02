DFA rules API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.

Function documentation
----------------------------------
DFA Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of all DFA functions--
    print(API.getASG_DFARules.__doc__)
    print(API.updateASG_DFARules.__doc__)
    print(API.getDFArules.__doc__)
    print(API.updateDFArule.__doc__)

Interface object documentation
-------------------------------------------------

DFA Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the DFA interface object and contained functions--
    print(InterfaceObjects.DFARule.__doc__)
    print(InterfaceObjects.DFARule.json2object.__doc__)
    print(InterfaceObjects.DFARule.object2json.__doc__)

Parameter Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Parameter interface object and contained functions--
    print(InterfaceObjects.Parameter.__doc__)

Fetch KB data
-------------------------------------

Fetching the DFA rules::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getDFARules.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the DFA rules
    DFARules_Selector = API.getASG_DFARules('ASG-1', "Selector")
    DFARules_Evaluator = API.getASG_DFARules('ASG-1', "Evaluator")

.. note:: The resolvePath() function will return the absolute path relative to the current directory

Update KB data
------------------------------------------------

Updating the DFA rules::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # --JSON import of DFA rules
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule_Selector.json')
    DFARule_Selector = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule_Evaluator.json')
    DFARule_Evaluator = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getDFARules.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #perform update
    error_S=API.updateASG_DFARules('ASG-1', "Selector",DFARule_Selector)
    error_E=API.updateASG_DFARules('ASG-1', "Evaluator",DFARule_Evaluator)

.. note:: The resolvePath() function will return the absolute path relative to the current directory

Add KB data
----------------------------------------------

Adding a single DFA rule::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # --JSON import of DFA rule
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFA_A.json')
    rule = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)

    # define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_addDFARule.pacopackage')

    # importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # perform update
    error_S = API.addASG_DFARule('ASG-1', "Selector", rule)

.. important:: DEVELOPER NOTE: DFA description not yet complete

Adding multiple DFA rule::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    ruleList = []
    # --JSON import of DFA rule
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFA_A.json')
    rule = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)
    ruleList.append(rule)

    # --JSON import of DFA rule
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFA_B.json')
    rule = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)
    ruleList.append(rule)

    # define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_addDFARules.pacopackage')

    # importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # perform update
    error_S = API.addASG_DFARules('ASG-1', "Selector",ruleList)

.. important:: DEVELOPER NOTE: DFA description not yet complete

Instantiating from JSON file
----------------------------------------------------------------

instantiating the DFA rule::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule.json')
    # instantiate the DFARule via the JSON file
    rule = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)


Generating JSON object
-----------------------------------------------------------------

Generating the DFA JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule.json')
    # instantiate the DFARule via the JSON file
    rule = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)

    #generating the JSON object
    rule_json = rule.object2json()
    #printing the JSON object
    print(rule_json)


