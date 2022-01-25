Assembly Sequence Generation Algorithm API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.

Calling the function documentation
----------------------------------
ASG Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all ASG functions--
    print(API.getASG.__doc__)
    print(API.updateASG_DFARules.__doc__)
    print(API.setASG.__doc__)

DFA Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all DFA functions--
    print(API.getASG_DFARules.__doc__)
    print(API.updateASG_DFARules.__doc__)
    print(API.getDFArules.__doc__)
    print(API.updateDFArule.__doc__)


Performance Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Performance functions--
    print(API.getPerformance.__doc__)
    print(API.updatePerformance.__doc__)
    print(API.setPerformance.__doc__)

Investigating the interface objects documentation
-------------------------------------------------

ASG Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the ASG interface object and contained functions--
    print(InterfaceObjects.ASG.__doc__)

DFA Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the DFA interface object and contained functions--
    print(InterfaceObjects.DFARule.__doc__)
    print(InterfaceObjects.DFARule.json2object.__doc__)
    print(InterfaceObjects.DFARule.object2json.__doc__)

Performance Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Performance interface object and contained functions--
    print(InterfaceObjects.PerformanceModel.__doc__)
    print(InterfaceObjects.PerformanceModel.json2object.__doc__)
    print(InterfaceObjects.PerformanceModel.object2json.__doc__)

Stopcondition Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Stopcondition interface object and contained functions--
    print(InterfaceObjects.StopCondition.__doc__)

Parameter Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Parameter interface object and contained functions--
    print(InterfaceObjects.Parameter.__doc__)

Objective Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Objective interface object and contained functions--
    print(InterfaceObjects.Objective.__doc__)


Constraint Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Constraint interface object and contained functions--
    print(InterfaceObjects.Constraint.__doc__)

DecisionVariable Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the DecisionVariable interface object and contained functions--
    print(InterfaceObjects.DecisionVariable.__doc__)


Fetching data from the Knowledge-base
-------------------------------------

Fetching the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getASG.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the ASG model
    InterfaceObject_received = API.getASG('ASG-1')

Fetching the DFA rules::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getDFARules.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the DFA rules
    DFARules_Selector = API.getASG_DFARules('ASG-1', "Selector")
    DFARules_Evaluator = API.getASG_DFARules('ASG-1', "Evaluator")

Fetching the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getPerformance.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the Performance model
    InterfaceObject_received = API.getPerformance('OPTIMIZATION-v1')


Updating existing data within the Knowledge-base
------------------------------------------------

Updating the ASG model:

.. warning:: Not yet implemented


Updating the DFA rules::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # --JSON import of DFA rules
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule_Selector.json')
    DFARule_Selector = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule_Evaluator.json')
    DFARule_Evaluator = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getDFARules.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    #perform update
    error_S=API.updateASG_DFARules('ASG-1', "Selector",DFARule_Selector)
    error_E=API.updateASG_DFARules('ASG-1', "Evaluator",DFARule_Evaluator)


Updating the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/updatePerformanceModel.json')
    interfaceObject = InterfaceObjects.PerformanceModel(jsonPath)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getPerformance.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    #perform update
    error = API.updatePerformance(interfaceObject)


Adding new data within a blank Knowledge-base
----------------------------------------------

Updating the ASG model:

.. warning:: Not yet implemented

Updating the DFA rules:

.. warning:: Not yet implemented

Updating the Performance model:

.. warning:: Not yet implemented

Instantiating Knowledge-base interface objects using a JSON file
----------------------------------------------------------------

instantiating the ASG model:

.. warning:: Not yet implemented


instantiating the DFA rule::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/DFARule.json')
    # instantiate the DFARule via the JSON file
    rule = InterfaceObjects.DFARule(JSONDescriptor=jsonDescriptor)


instantiating the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/PerformanceModel.json')
    # instantiate the Performance model via the JSON file
    pModel = InterfaceObjects.PerformanceModel(jsonDescriptor)


Generating JSON objects from the Knowledge-base interface objects
-----------------------------------------------------------------


Generating the ASG JSON model:

.. warning:: Not yet implemented


Generating the Performance JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/PerformanceModel.json')
    # instantiate the Performance model via the JSON file
    pModel = InterfaceObjects.PerformanceModel(jsonDescriptor)

    #generating the JSON object
    pModel_json = pModel.object2json()
    #printing the JSON object
    print(pModel_json)


