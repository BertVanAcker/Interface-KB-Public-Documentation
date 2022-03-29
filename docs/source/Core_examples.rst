KB CORE API examples
===================================================
This section describes some usage examples of the Knowledge-Base Interface.

Function documentation
----------------------------------

Product Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Product functions--
    print(API.getProduct.__doc__)
    print(API.updateProduct.__doc__)
    print(API.setProduct.__doc__)

Product Part Function documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Product Part functions--
    print(API.getProductPart.__doc__)
    print(API.updateProductPart.__doc__)
    print(API.setProductPart.__doc__)
    print(API.getAllProductParts.__doc__)
    print(API.updateAllProductParts.__doc__)
    print(API.setAllProductParts.__doc__)


Assembly sequence documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of all Assembly sequence functions--
    print(API.getAssemblySequence.__doc__)
    print(API.updateAssemblySequence.__doc__)
    print(API.setAssemblySequence.__doc__)

Interface object documentation
-------------------------------------------------

Product Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the DFA interface object and contained functions--
    print(InterfaceObjects.Product.__doc__)
    print(InterfaceObjects.Product.object2json.__doc__)
    print(InterfaceObjects.Product.json2object.__doc__)

Parameter Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Parameter interface object and contained functions--
    print(InterfaceObjects.Parameter.__doc__)

Product Part Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the DFA interface object and contained functions--
    print(InterfaceObjects.ProductPart.__doc__)
    print(InterfaceObjects.ProductPart.object2json.__doc__)
    print(InterfaceObjects.ProductPart.json2object.__doc__)

Assembly Sequence Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the AssemblySequence interface object and contained functions--
    print(InterfaceObjects.AssemblySequence.__doc__)
    print(InterfaceObjects.AssemblySequence.object2json.__doc__)
    print(InterfaceObjects.AssemblySequence.json2object.__doc__)

Operation Interface objects documentation::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    #--Call information of the Operation interface object and contained functions--
    print(InterfaceObjects.Operation.__doc__)
    print(InterfaceObjects.Operation.object2json.__doc__)
    print(InterfaceObjects.Operation.json2object.__doc__)

Create KB from scratch
-------------------------------------

Creating an empty Knowledge-Base::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Create New_KB_TEST.pacopackage in output/KB_Instance/
    API.createEmptyKB(Name="New_KB_TEST", OutputPath="output/KB_Instance/")

Fetch KB data
-------------------------------------

Fetching the Product::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/OldGearBox.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the Product
    InterfaceObject_received = API.getProduct()


.. important:: Currently, no parameters are fetched from the KB!

Fetching the Product Part::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/OldGearBox.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the Product Part
    InterfaceObject_received = API.getProductPart('(3) Input Shaft')


.. important:: Currently, no contact features are fetched from the KB!

Fetching all contained Product Parts::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/OldGearBox.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching all Product Parts
    InterfaceObjectList = API.getAllProductParts()

.. important:: Currently, no contact features are fetched from the KB!

Fetching the Assembly Sequence of a single Assembly System::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getAssemblySequence.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the assembly sequence of Assembly System AS-1
    InterfaceObject_received = API.getAssemblySequence("AS-1")


Update KB data
------------------------------------------------

Update the Product::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # --Product interface object
    interfaceObject = InterfaceObjects.Product(Name='OldGearBox',STEPFile='c:/NEW/PATH/TO/THE/STEPFILE')

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/OldGearBox.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # updating the Product model
    error = API.updateProduct(interfaceObject=interfaceObject)

.. important:: Currently, no parameters are updated within the KB!


Update the Product Part::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/updateProductPart.json')
    interfaceObject = InterfaceObjects.ProductPart(jsonPath)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateProductPart.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # updating the Product Part model
    error = API.updateProductPart(interfaceObject)

.. important:: Currently, no contact features are updated within the KB!


Update all contained Product Parts::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    interfaceObjectList = []

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/InputShaft.json')
    interfaceObject1 = InterfaceObjects.ProductPart(jsonPath)
    interfaceObjectList.append(interfaceObject1)

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/SmallGear.json')
    interfaceObject2 = InterfaceObjects.ProductPart(jsonPath)
    interfaceObjectList.append(interfaceObject2)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_updateProductPart.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # perform update
    error = API.updateAllProductParts(interfaceObjectList)

.. important:: Currently, no contact features are updated within the KB!

Update the Assembly Sequence of a single Assembly System:

.. important:: Not supported - use add function


Add KB data
----------------------------------------------

Adding the Product::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # load the json file to perform setter function
    interfaceObject = InterfaceObjects.Product(Name='OldGearBox', STEPFile='c:/NEW/PATH/TO/THE/STEPFILE')

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_setProduct.pacopackage')
    API.KB_path = path_KB  # To update current KB
    API.ECORE_path = path_ecore  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # Adding a new Product Part model
    error = API.setProduct(interfaceObject=interfaceObject)

.. important:: DEVELOPER NOTE: functions does not work yet -> discuss the dependencies that need to be set while adding a Product

Adding the Product Part::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/addProductPart.json')
    interfaceObject = InterfaceObjects.ProductPart(jsonPath)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_addProductPart.xmi')
    API.KB_path = path_KB  # To update current KB
    API.ECORE_path = path_ecore  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # Adding a new Product Part model
    error = API.setProductPart(interfaceObject)

.. important:: DEVELOPER NOTE: Model(+parameters) and Material are not set correctly -> not linked


Adding all Product Parts::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    interfaceObjectList = []

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/ProductPart_A.json')
    interfaceObject1 = InterfaceObjects.ProductPart(jsonPath)
    interfaceObjectList.append(interfaceObject1)

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/ProductPart_B.json')
    interfaceObject2 = InterfaceObjects.ProductPart(jsonPath)
    interfaceObjectList.append(interfaceObject2)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_addProductPart.xmi')
    API.KB_path = path_KB  # To update current KB
    API.ECORE_path = path_ecore  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # Adding a new Product Part model
    error = API.setAllProductParts(interfaceObjectList)

.. important:: DEVELOPER NOTE: Model(+parameters) and Material are not serialized

Adding a Assembly Sequence to an existing Assembly System::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(False)

    # create an empty KB model
    API.createEmptyKB(Name="test_setAssemblySequence_empty", OutputPath="output/")

    # load the json file to perform update
    jsonPath = API.resolvePath('input/JSON-docs/AssemblySequence.json')
    interfaceObject = InterfaceObjects.AssemblySequence(JSONDescriptor=jsonPath, DEBUG=False)

    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    path_KB = API.resolvePath('output/test_setAssemblySequence_empty.pacopackage')  # TODO: make version where no Product is defined!
    API.KB_path = path_KB  # To update current KB
    API.ECORE_path = path_ecore
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # updating the ASssembly Sequence and add to Assembly System
    error = API.setAssemblySequence(AssemblySystemName="TEST_AS",InterfaceObject=interfaceObject)

.. important:: Not yet serializable

Instantiating from JSON file
----------------------------------------------------------------

Instantiate the Product model ::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/Product.json')
    # instantiate the DFARule via the JSON file
    product = InterfaceObjects.Product(JSONDescriptor=jsonDescriptor)

Instantiate the Product Part model ::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # Specify the absolute path to the JSON file
    jsonDescriptor = API.resolvePath('input/JSON-docs/ProductPart.json')
    # instantiate the DFARule via the JSON file
    productPart = InterfaceObjects.ProductPart(JSONDescriptor=jsonDescriptor)


Instantiate the Assembly Sequence model :

.. important:: Not yet implemented -> recursiveness depth?

Generating JSON object
-----------------------------------------------------------------

Generating the Product JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # --Product interface object
    product = InterfaceObjects.Product(Name='OldGearBox',STEPFile='c:/NEW/PATH/TO/THE/STEPFILE')

    #generating the JSON object
    product_json = product.object2json()
    #printing the JSON object
    print(product_json)

Generating the Product Part JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version5/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/OldGearBox.xmi')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the Product Part
    productPart = API.getProductPart('(3) Input Shaft')

    #generating the JSON object
    productPart_json = productPart.object2json()
    #printing the JSON object
    print(productPart_json)


Generating the Assembly Sequence JSON model::

    from Interface_KB import KB_Interface,InterfaceObjects
    API = KB_Interface.KB_Interface(True)

    # specify the KB metamodel
    path_ecore = API.resolvePath('input/metamodel/Version-6-1/PACoMM.ecore')
    #define the path to the KB instance model
    path_KB = API.resolvePath('input/KB_examples/test_getAssemblySequence.pacopackage')
    API.KB_path = path_KB  # To update current KB
    #importing the KB instance model
    API.model = API.importInstanceModel(path_ecore, path_KB)

    # fetching the assembly sequence of Assembly System AS-1
    AssemblySequence = API.getAssemblySequence("AS-1")

    #generating the JSON object
    AssemblySequence_json = AssemblySequence.object2json()
    #printing the JSON object
    print(AssemblySequence_json)
