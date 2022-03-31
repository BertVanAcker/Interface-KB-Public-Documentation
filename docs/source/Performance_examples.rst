Performance (optimization) API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.

Function documentation
----------------------------------
Performance Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Performance functions--
    print(API.getPerformance.__doc__)
    print(API.updatePerformance.__doc__)
    print(API.setPerformance.__doc__)

Interface objects documentation
-------------------------------------------------

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


Fetch KB data
-------------------------------------

Fetching the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getPerformance.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    # fetching the Performance model
    InterfaceObject_received = API.getPerformance('OPTIMIZATION-v1')


Update KB data
----------------------------------------------

Updating the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/updatePerformanceModel.json')
    interfaceObject = InterfaceObjects.PerformanceModel(jsonPath)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateASG.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    #perform update
    error = API.updatePerformance(interfaceObject)

Add KB data
----------------------------------------------

Adding the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/setPerformanceModel.json')
    interfaceObject = InterfaceObjects.PerformanceModel(jsonPath)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateASG.pacopackage')
    API.KB_path = path_KB  # To update current KB
    API.ECORE_path = path_ecore
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    #perform adding the performance model
    error = API.setPerformance(interfaceObject)

.. important:: DEVELOPER NOTE: Stopconditions and  Expressions not added yet!

Instantiating from JSON file
----------------------------------------------------------------

instantiating the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/PerformanceModel.json')
    # instantiate the Performance model via the JSON file
    pModel = InterfaceObjects.PerformanceModel(jsonDescriptor)



Generating JSON object
-----------------------------------------------------------------

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


