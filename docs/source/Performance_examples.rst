Performance (optimization) API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.

Function documentation
----------------------------------
Performance Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of all Performance functions--
    print(API.getPerformance.__doc__)
    print(API.updatePerformance.__doc__)
    print(API.setPerformance.__doc__)
    print(API.getAnalysisModel.__doc__)
    print(API.updateAnalysisModel.__doc__)
    print(API.setAnalysisModel.__doc__)
    getAnalysisModel

Interface objects documentation
-------------------------------------------------

Performance Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Performance interface object and contained functions--
    print(InterfaceObjects.PerformanceModel.__doc__)
    print(InterfaceObjects.PerformanceModel.json2object.__doc__)
    print(InterfaceObjects.PerformanceModel.object2json.__doc__)

Stopcondition Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Stopcondition interface object and contained functions--
    print(InterfaceObjects.StopCondition.__doc__)

Parameter Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Parameter interface object and contained functions--
    print(InterfaceObjects.Parameter.__doc__)

Objective Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Objective interface object and contained functions--
    print(InterfaceObjects.Objective.__doc__)


Constraint Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Constraint interface object and contained functions--
    print(InterfaceObjects.Constraint.__doc__)

DecisionVariable Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the DecisionVariable interface object and contained functions--
    print(InterfaceObjects.DecisionVariable.__doc__)

Analysis Model Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #--Call information of the Performance interface object and contained functions--
    print(InterfaceObjects.AnalysisModel.__doc__)
    print(InterfaceObjects.AnalysisModel.json2object.__doc__)
    print(InterfaceObjects.AnalysisModel.object2json.__doc__)
Fetch KB data
-------------------------------------

Fetching the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getPerformance.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the Performance model
    InterfaceObject_received = API.getPerformance('OPTIMIZATION-v1')


Fetching the Analysis model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getAnalysisModel.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    # fetching the Performance model
    InterfaceObject_received = API.getAnalysisModel('AnalysisModel_v1')

Update KB data
----------------------------------------------

Updating the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/updatePerformanceModel.json')
    interfaceObject = InterfaceObjects.PerformanceModel(jsonPath)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateASG.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #perform update
    error = API.updatePerformance(interfaceObject)

Updating the Analysis model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #set the interface objects
    Contacts = [Contact(Name="Contact1", Type="TEST",SearchDistance=5.0,ApplicationAreas=[['AA_1',None]])]
    BoundaryConditions = [BoundaryCondition(Name="BC_001", Type="Unknown",Value=21.0,Direction=[0.0,1.0,1.0,1.0,0.0,1.0],DOF=[False,True,False,True,True,False],ApplicationAreas=[['AA_1',None]])]
    interfaceObject = AnalysisModel(Name='AnalysisModel_v1',
                                    Description="[UPDATE] This is a description of the analysis model",
                                    Version="0.0.2", GUID="", AnalysisType="",
                                    ModelFile="C:/location/pointing/to/NEWmodelfile", SubsetNumber=6.0,
                                    ModelDescription=["stl", "0.0.2", "JEAN VAN"], Contacts=Contacts,BoundaryConditions=BoundaryConditions,DecisionVariables=[],ApplicationAreas=[],DEBUG=True)



    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_UpdateAnalysisModel.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #perform update
    error = API.updateAnalysisModel(interfaceObject)

Add KB data
----------------------------------------------

Adding the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/setPerformanceModel.json')
    interfaceObject = InterfaceObjects.PerformanceModel(jsonPath)

    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateASG.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #perform adding the performance model
    error = API.setPerformance(interfaceObject)

Adding the Analysis model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    #create an empty KB model
    API.createEmptyKB(Name="New_KB_ANALYSIS", OutputPath="output/KB_Instance/")

    # set a product (no product = no analysis possible)
    producteObject = InterfaceObjects.Product(Name='OldGearBox', STEPFile='c:/NEW/PATH/TO/THE/STEPFILE')

    #set the interface objects
    Contacts = [Contact(Name="Contact1", Type="TEST",SearchDistance=5.0,ApplicationAreas=[['AA_1',None]])]
    BoundaryConditions = [BoundaryCondition(Name="BC_001", Type="Unknown",Value=21.0,Direction=[0.0,1.0,1.0,1.0,0.0,1.0],DOF=[False,True,False,True,True,False],ApplicationAreas=[['AA_1',None]])]
    interfaceObject = AnalysisModel(Name='AnalysisModel_v1',
                                    Description="[UPDATE] This is a description of the analysis model",
                                    Version="0.0.2", GUID="", AnalysisType="",
                                    ModelFile="C:/location/pointing/to/NEWmodelfile", SubsetNumber=6.0,
                                    ModelDescription=["stl", "0.0.2", "JEAN VAN"], Contacts=Contacts,BoundaryConditions=BoundaryConditions,DecisionVariables=[],ApplicationAreas=[],DEBUG=True)

    #define the path to the KB instance model
    path_KB = API.resolvePath('output/KB_Instance/New_KB_ANALYSIS.pacopackage')

    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importKBInstanceModel(path_KB)

    #set the product
    error = API.setProduct(interfaceObject=producteObject)

    #Reload + set the analysis
    self.MM, self.model, self.model_instance = API.importKBInstanceModel(path_KB)
    error = API.setAnalysisModel(analysisObject)

Instantiating from JSON file
----------------------------------------------------------------

instantiating the Performance model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/PerformanceModel.json')
    # instantiate the Performance model via the JSON file
    pModel = InterfaceObjects.PerformanceModel(jsonDescriptor)



Generating JSON object
-----------------------------------------------------------------

Generating the Performance JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(KB_BASELINE='input/metamodel/Version8/PACoMM.ecore',DEBUG=True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/PerformanceModel.json')
    # instantiate the Performance model via the JSON file
    pModel = InterfaceObjects.PerformanceModel(jsonDescriptor)

    #generating the JSON object
    pModel_json = pModel.object2json()
    #printing the JSON object
    print(pModel_json)


