Assembly Sequence Generation Algorithm API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.


Function documentation
----------------------------------
ASG Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all ASG functions--
    print(API.getASG.__doc__)
    print(API.updateASG_DFARules.__doc__)
    print(API.setASG.__doc__)

Interface object documentation
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

Parameter Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Parameter interface object and contained functions--
    print(InterfaceObjects.Parameter.__doc__)

Fetch KB data
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
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    # fetching the ASG model
    InterfaceObject_received = API.getASG('ASG-1')


Update KB data
----------------------------------------------

Updating the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/updateASGModel.json')
    interfaceObject = InterfaceObjects.ASG(jsonPath)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getASG.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    #updating the ASG model
    error = API.updateASG(AssemblySystemName='ASG-1',interfaceObject=interfaceObject)


Add KB data
----------------------------------------------

Adding the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #------------------------specify interface object START -----------------------------
    stopConditions = []
    s1 = InterfaceObjects.StopCondition(None,"Stop-1","Maximum depth of search",1000.0,"maxDepth=0")
    s2 = InterfaceObjects.StopCondition(None, "Stop-2","Maximum time of search",360.0,"maxDepth=1")
    stopConditions.append(s1)
    stopConditions.append(s2)
    ASG_interface = InterfaceObjects.ASG(None,Name='ASG-1-config', Description='AssemblySequenceDraft1',ProcessingType="Full=0",Generator=['GenNew-1','SinglePartGenerator'],Selector=['SelNew-1','RuleSelector'],Evaluator=['EvalNew-1','RuleEvaluator'],StopConditions=stopConditions)
    # ------------------------specify interface object END  -----------------------------

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_setASG.pacopackage')
    API.KB_path = path_KB  # To update current KB
    API.ECORE_path = path_ecore
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    #updating the ASG model
    error = API.setASG('ASG-1',ASG_interface)


Instantiating from JSON file
----------------------------------------------------------------

instantiating the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/updateASGModel.json')
    # instantiate the DFARule via the JSON file
    ASG = InterfaceObjects.ASG(JSONDescriptor=jsonDescriptor)


Generating JSON object
-----------------------------------------------------------------


Generating the ASG JSON model::

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateASG.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    # fetching the ASG model
    InterfaceObject_received = API.getASG('ASG-1')

    #generating the JSON object
    ASG_json = InterfaceObject_received.object2json()
    #printing the JSON object
    print(ASG_json)


