Contract-Based Co-Design API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.

Function documentation
----------------------------------
Contract Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Contract functions--
    print(API.getContract.__doc__)
    print(API.updateContract.__doc__)
    print(API.setContract.__doc__)

Ontology Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Ontology functions--
    print(API.getOntology.__doc__)
    print(API.updateOntology.__doc__)
    print(API.setOntology.__doc__)

Interface objects documentation
-------------------------------------------------

Contract Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Contract interface object and contained functions--
    print(InterfaceObjects.Contract.__doc__)
    print(InterfaceObjects.Contract.json2object.__doc__)
    print(InterfaceObjects.Contract.object2json.__doc__)

Ontology Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Ontology interface object and contained functions--
    print(InterfaceObjects.Ontology.__doc__)
    print(InterfaceObjects.Ontology.json2object.__doc__)
    print(InterfaceObjects.Ontology.object2json.__doc__)

Relation Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Relation interface object and contained functions--
    print(InterfaceObjects.Relation.__doc__)
    print(InterfaceObjects.Relation.json2object.__doc__)
    print(InterfaceObjects.Relation.object2json.__doc__)

Domain variable Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the DomainVariable interface object and contained functions--
    print(InterfaceObjects.DomainVariable.__doc__)
    print(InterfaceObjects.DomainVariable.json2object.__doc__)
    print(InterfaceObjects.DomainVariable.object2json.__doc__)

Fetch KB data
-------------------------------------

Fetching the contract model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version7/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/ContractOntology_example1.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    # fetching the contract model
    InterfaceObject_received = API.getContract('C-1')

Fetching the ontology model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version7/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/ContractOntology_example1.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.MM, API.model, API.model_instance = API.importInstanceModel_NEW(path_ecore, path_KB)

    # fetching the ontology model
    InterfaceObject_received = API.getOntology()


Update KB data
----------------------------------------------

Updating the Contract model:

.. important:: Not yet implemented

Updating the Ontology model:

.. important:: Not yet implemented


Add KB data
----------------------------------------------

Adding the Contract model:

.. important:: Not yet implemented

Adding the Ontology model:

.. important:: Not yet implemented

Instantiating from JSON file
----------------------------------------------------------------

instantiating the Contract model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/Contract.json')
    # instantiate the Contract model via the JSON file
    cModel = InterfaceObjects.Contract(jsonDescriptor)


instantiating the Ontology model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/Ontology.json')
    # instantiate the Ontology model via the JSON file
    oModel = InterfaceObjects.Ontology(jsonDescriptor)


Generating JSON object
-----------------------------------------------------------------

Generating the Contract JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version7/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/ContractOntology_example1.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the Performance model
    contract = API.getContract('C-1')

    #generating the JSON object
    contract_json = contract.object2json()
    #printing the JSON object
    print(contract_json)

Generating the Ontology JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version7/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/ContractOntology_example1.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the Performance model
    ontology = API.getOntology()

    #generating the JSON object
    ontology_json = ontology.object2json()
    #printing the JSON object
    print(ontology_json)

