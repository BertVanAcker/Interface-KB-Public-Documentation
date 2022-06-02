Assembly Sequence Generation Algorithm API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.


Function documentation
----------------------------------
ASG Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of all ASG functions--
    print(API.getASG.__doc__)
    print(API.updateASG_DFARules.__doc__)
    print(API.setASG.__doc__)
    print(API.getASGAlgorithmData.__doc__)
    print(API.updateASGAlgorithmData.__doc__)
    print(API.setASGAlgorithmData.__doc__)


Interface object documentation
-------------------------------------------------

ASG Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the ASG interface object and contained functions--
    print(InterfaceObjects.ASG.__doc__)

ASG Data Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the ASG interface object and contained functions--
    print(ASGAlgorithmData.ASG.__doc__)



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

Fetching the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getASG.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the ASG model
    InterfaceObject_received = API.getASG('ASG-1')

Fetching the ASG Data::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/ASGAlgorithmData_TEST.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the ASG data
    InterfaceObject_received = API.getASGAlgorithmData('ASG-01')

Update KB data
----------------------------------------------

Updating the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/updateASGModel.json')
    interfaceObject = InterfaceObjects.ASG(jsonPath)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getASG.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #updating the ASG model
    error = API.updateASG(AssemblySystemName='ASG-1',interfaceObject=interfaceObject)

Updating the ASG Data::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #interface object to be updated
    interfaceObject = InterfaceObjects.ASGAlgorithmData(Score=6.0,Feasible=False,UnexploredOptions="Option2",Priority=2.0)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/UpdateASGAlgorithmData.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # Update the ASG data
    InterfaceObject_received = API.updateASGAlgorithmData(AssemblySystemName='ASG-01', interfaceObject=interfaceObject)

Add KB data
----------------------------------------------

Adding the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #------------------------specify interface object START -----------------------------
    stopConditions = []
    s1 = InterfaceObjects.StopCondition(None,"Stop-1","Maximum depth of search",1000.0,"maxDepth=0")
    s2 = InterfaceObjects.StopCondition(None, "Stop-2","Maximum time of search",360.0,"maxDepth=1")
    stopConditions.append(s1)
    stopConditions.append(s2)
    ASG_interface = InterfaceObjects.ASG(None,Name='ASG-1-config', Description='AssemblySequenceDraft1',ProcessingType="Full=0",Generator=['GenNew-1','SinglePartGenerator'],Selector=['SelNew-1','RuleSelector'],Evaluator=['EvalNew-1','RuleEvaluator'],StopConditions=stopConditions)
    # ------------------------specify interface object END  -----------------------------

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_setASG.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #updating the ASG model
    error = API.setASG('ASG-1',ASG_interface)

Adding the ASG Data::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #interface object to be updated
    interfaceObject = InterfaceObjects.ASGAlgorithmData(Score=6.0,Feasible=False,UnexploredOptions="Option2",Priority=2.0)

    #define the path to the KB instance model
    path_KB = API.resolvePath('output/KB_Instance/test_setASGData_EmptyKB.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # Add the ASG data
    InterfaceObject_received = API.setASGAlgorithmData('ASG-NEW',interfaceObject)


Instantiating from JSON file
----------------------------------------------------------------

instantiating the ASG model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/updateASGModel.json')
    # instantiate the DFARule via the JSON file
    ASG = InterfaceObjects.ASG(JSONDescriptor=jsonDescriptor)


Generating JSON object
-----------------------------------------------------------------


Generating the ASG JSON model::

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateASG.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the ASG model
    InterfaceObject_received = API.getASG('ASG-1')

    #generating the JSON object
    ASG_json = InterfaceObject_received.object2json()
    #printing the JSON object
    print(ASG_json)

Generating the ASG Data JSON model::

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/ASGAlgorithmData_TEST.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the ASG model
    InterfaceObject_received = API.getASGAlgorithmData('ASG-01')

    #generating the JSON object
    ASG_json = InterfaceObject_received.object2json()
    #printing the JSON object
    print(ASG_json)
