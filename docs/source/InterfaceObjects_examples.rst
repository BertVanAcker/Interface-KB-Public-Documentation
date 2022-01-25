Interface Objects JSON examples
===================================================
This section gives some examples of interface objects in JSON format

Product JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

    {
        "DEBUG": true,
        "Name": "OldGearBox",
        "Description": "",
        "STEPFile": "c:/NEW/PATH/TO/THE/STEPFILE",
        "parameterList": [
            {
                "DEBUG": true,
                "Name": "Parameter1",
                "Description": "First parameter",
                "Key": "",
                "GUID": "PAR1",
                "Value": 10.0,
                "StopCriteria": "maxDepth=0"
            },
            {
                "DEBUG": true,
                "Name": "Parameter2",
                "Description": "Second parameter",
                "Key": "",
                "GUID": "PAR2",
                "Value": 81.0,
                "StopCriteria": "maxDepth=0"
            }
        ]
    }

Product Part JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

    {
        "DEBUG": true,
        "Name": "(3) Input Shaft",
        "Description": "Description NEW",
        "ProductType": "Unknown",
        "Quantity": 115,
        "parameterList": [
            {
                "DEBUG": true,
                "Name": "Name NEW",
                "Description": "",
                "Key": "Input",
                "GUID": "",
                "Value": "[10mm]",
                "StopCriteria": "Not defined"
            },
            {
                "DEBUG": true,
                "Name": "Name NEW",
                "Description": "",
                "Key": "Output",
                "GUID": "",
                "Value": "[50Nm^-1]",
                "StopCriteria": "Not defined"
            }
        ],
        "partList": [
            {
                "DEBUG": true,
                "Name": "(8) Small Gear",
                "Description": "Description NEW",
                "ProductType": "GEAR",
                "Quantity": 1,
                "parameterList": [],
                "partList": [],
                "material": [
                    "Structural Steel(SS)",
                    0.0,
                    0.0,
                    7850.0,
                    0.0,
                    ""
                ]
            }
        ],
        "material": [
            "Structural Steel(SS)",
            0.0,
            0.0,
            7850.0,
            0.0,
            ""
        ]
    }

Assembly Sequence JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

   {
        "DEBUG": true,
        "Name": "SUB-1",
        "Description": "NOT IN MM",
        "AssemblyMetric": [
            "OP-1",
            "0.89"
        ],
        "AssemblyOptions": [
            "SUB-1",
            [
                {
                    "DEBUG": true,
                    "Name": "SCREW-2-3",
                    "Description": "NOT IN MM",
                    "Fastners": [
                        "Part-1"
                    ],
                    "OperationMetric": [
                        "OP-2",
                        "0.57"
                    ],
                    "Operators": [
                        [
                            "Joachim",
                            65.0,
                            180.0,
                            55.0,
                            120.0
                        ]
                    ],
                    "Tool": [
                        [
                            "Screwdriver-1",
                            150.0,
                            0.0,
                            "0.0.0.0",
                            "c:/../../../",
                            [
                                "Joachim"
                            ]
                        ]
                    ]
                }
            ],
            [
                [
                    "SUB-2",
                    [],
                    []
                ],
                [
                    "SUB-3",
                    [
                        {
                            "DEBUG": true,
                            "Name": "SCREW-4-5",
                            "Description": "NOT IN MM",
                            "Fastners": [
                                "Part-1",
                                "Part-2"
                            ],
                            "OperationMetric": [
                                "OP-2",
                                "0.57"
                            ],
                            "Operators": [
                                [
                                    "Moharram",
                                    65.0,
                                    175.0,
                                    110.0,
                                    60.0
                                ]
                            ],
                            "Tool": [
                                [
                                    "Screwdriver-1",
                                    150.0,
                                    0.0,
                                    "0.0.0.0",
                                    "c:/../../../",
                                    [
                                        "Moharram"
                                    ]
                                ]
                            ]
                        }
                    ],
                    [
                        [
                            "SUB-4",
                            [],
                            []
                        ],
                        [
                            "SUB-5",
                            [],
                            []
                        ]
                    ]
                ]
            ]
        ]
    }



DFA Rule JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

    {
        "DFARule": {
            "Name": "rule-height-max",
            "Description": "Hello World",
            "RuleType": "DFA_MaxValue",
            "isAppliedToProduct": "True",
            "isAppliedToProductPart": "False",
            "isAppliedToAssemblySequence": "False",
            "hasScorePropagation": "0",
            "hasScoreType": "0",
            "optionList": [
                {
                    "Name": "TE",
                    "Value1": "True",
                    "Value2": "None"
                },
                {
                    "Name": "Option1",
                    "Value1": "OptionEnumSelect",
                    "Value2": "None"
                }
            ],
            "property": [
              {
                    "Name": "Weight",
                    "Value1": "100.0",
                    "Value2": "None"
                }

            ]
        }
    }

Performance model JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

    {
        "DEBUG": true,
        "Name": "OPTIMIZATION-v1",
        "Description": "Optimization problem v1",
        "OptimizationMethod": [
            "HEURISTIC-M01",
            "Heuristic method",
            "Heuristic"
        ],
        "StopConditionList": [
            {
                "DEBUG": true,
                "Name": "STOP-1",
                "Description": "Stop criterion 1",
                "Value": 3600.0,
                "StopCriteria": "maxTime"
            },
            {
                "DEBUG": true,
                "Name": "STOP-2",
                "Description": "Stop criterion 2",
                "Value": 15001.0,
                "StopCriteria": "maxDepth"
            }
        ],
        "MethodPerformance": [],
        "RAWResults": [],
        "interpretedResults": [],
        "parameterList": [
            {
                "DEBUG": true,
                "Name": "Mass_var",
                "Description": "Total mass variable",
                "InitialValue": 10.0,
                "MinValue": 10.0,
                "MaxValue": 100.0,
                "Optimum": 81.0,
                "Resolution": 0.1,
                "parameterList": [
                    {
                        "DEBUG": true,
                        "Name": "Mass",
                        "Description": "Total mass parameter",
                        "Key": "MASS",
                        "GUID": null,
                        "Value": null,
                        "StopCriteria": "maxDepth=0"
                    }
                ]
            }
        ],
        "ObjectiveList": [
            {
                "DEBUG": true,
                "Name": "MIN-MASS",
                "Description": "Minimize the total mass",
                "ObjectiveOption": [
                    "Mass_var",
                    "Total mass variable",
                    81.0
                ]
            }
        ],
        "ConstraintList": [
            {
                "DEBUG": true,
                "Name": "CONSTRAINT1",
                "Description": "Constraint1",
                "Expression": [
                    [
                        "LEFT",
                        "Mass_var",
                        "Total mass variable",
                        81.0
                    ],
                    [
                        "RIGHT",
                        85.0
                    ],
                    "<"
                ]
            }
        ]
    }

ASG JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

   {
        "DEBUG": true,
        "Name": "ASG-1-config",
        "Description": "AssemblySequenceDraft1 NEW",
        "ProcessingType": "Full",
        "Generator": [
            "Gen-1 NEW",
            "SinglePartGenerator"
        ],
        "Selector": [
            "Sel-1 NEW",
            "RuleSelector"
        ],
        "SelectorDFARuleList": [],
        "Evaluator": [
            "Eval-1 NEW",
            "RuleEvaluator"
        ],
        "EvaluatorDFARuleList": [],
        "StopConditionList": [
            {
                "DEBUG": true,
                "Name": "Stop-1",
                "Description": "Maximum depth of search NEW",
                "Value": 100.0,
                "StopCriteria": "maxDepth"
            },
            {
                "DEBUG": true,
                "Name": "Stop-2",
                "Description": "Maximum time of search NEW",
                "Value": 3600.0,
                "StopCriteria": "maxTime"
            }
        ]
    }

Contract JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

    {
        "DEBUG": true,
        "Name": "C-1",
        "Description": "Co-desgin contract C-1",
        "Assumptions": [
            [
                {
                    "DEBUG": true,
                    "Name": "Lid weight",
                    "Description": null,
                    "Unit": "kg"
                },
                "<",
                10.0
            ],
            [
                {
                    "DEBUG": true,
                    "Name": "NumberOfParts",
                    "Description": null,
                    "Unit": "-"
                },
                "<",
                10.0
            ],
            [
                {
                    "DEBUG": true,
                    "Name": "NumberOfParts",
                    "Description": null,
                    "Unit": "-"
                },
                ">=",
                2.0
            ]
        ],
        "Guarantees": [
            [
                {
                    "DEBUG": true,
                    "Name": "Assembalibility score",
                    "Description": null,
                    "Unit": "-"
                },
                ">=",
                0.85
            ],
            [
                {
                    "DEBUG": true,
                    "Name": "Stiffness",
                    "Description": null,
                    "Unit": "N/m"
                },
                ">=",
                15000.0
            ]
        ]
    }

Ontology JSON
----------------------------------
Example interface object in JSON format:

.. code-block::

    {
        "DEBUG": true,
        "Name": "Not in MM",
        "Description": "Not in MM",
        "Relations": [
            {
                "DEBUG": true,
                "Name": "FootprintStiffness",
                "Description": null,
                "Source": {
                    "DEBUG": true,
                    "Name": "House footprint",
                    "Description": null,
                    "Unit": "mm2"
                },
                "Destination": {
                    "DEBUG": true,
                    "Name": "Stiffness",
                    "Description": null,
                    "Unit": "N/m"
                },
                "SensitivityDirection": "Positive",
                "Weight": 0.0
            },
            {
                "DEBUG": true,
                "Name": "WeightAssembelebility",
                "Description": null,
                "Source": {
                    "DEBUG": true,
                    "Name": "Lid weight",
                    "Description": null,
                    "Unit": "kg"
                },
                "Destination": {
                    "DEBUG": true,
                    "Name": "Assembalibility score",
                    "Description": null,
                    "Unit": "-"
                },
                "SensitivityDirection": "Negative",
                "Weight": 0.0
            }
        ]
    }



