---
title: Análisis de sistemas.
date: Last Modified
permalink: /analisis/
eleventyNavigation:
    key: analisis
    order: 5
    title: Análisis de sistemas.
---

<!-- @format -->

## **Introducción**

[Documentacion PlantUML](https://plantuml.com/es/)  
[PlantUML C4](https://github.com/plantuml-stdlib/C4-PlantUML)  
[Generador de Diagramas PlantUML](http://www.plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000)  
[Eleventy - Generador de Sites](https://www.11ty.dev/docs/languages/markdown/)  
[Theme para la documentacion](https://spacebook.app/)  
[PlantUML Server en Docker](https://hub.docker.com/r/plantuml/plantuml-server)

# Ejemplo UML:

<!--
```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Deployment.puml

    ' default header Property, Value
    AddProperty("Name", "Flash")
    AddProperty("Organization", "Zootopia")
    AddProperty("Tool", "Internet Explorer 7.0")
    Person(personAlias, "Label", "Optional Description (with default property header)")

    SetPropertyHeader("Property","Value", "Description")
    AddProperty("Prop1", "Value1", "Details1")
    AddProperty("Prop2", "Value2", "Details2")

    Deployment_Node_L(nodeAlias, "Label", "Optional Type", "Optional Description (with custom property header)") {
        WithoutPropertyHeader()
        AddProperty("PropC1", "ValueC1")
        AddProperty("PropC2", "ValueC2")
        Container(containerAlias, "Label", "Technology", "Optional Description (without property header)")
    }

    System(systemAlias, "Label", "Optional Description (without properties)")

    Rel(personAlias, containerAlias, "Label", "Optional Technology")

@enduml
``` -->

![Diagrama](http://www.plantuml.com/plantuml/png/ZP91ZzCm48Nl_HKc5x9Ijs4h92HEk-g2G2gx5HIGk5HkCZIM9XxB7gi4n7_7DabJQ5h8nHFdlNdvnhvrB2tx1YTFb2xHLo1gPkDU5eML-zbESUstte4jIJDedfNK50QbZfvhnnMgRR5uVhsAMn_VBOj6EWORjZRtO93Q9ffC39Y8y3mL5NoL7bdK82kmOcN9WELsAZv9z914TrNLR-VPWsmWcuhiDKfNPrUdWaUxarfzbwn8H-4N8YQZv9XsJOHHypR0M0qiNdqpI1QiU35xrXbMO1tftAJb3fLqmR2KMqZEHnDp98fxSALLwKta-p2d0vdfuZh4gz0tDVu0tF_9c_Gbp_htR9eb_9Xmr7WC8LOtKPSCiGeEbWhTpJdv_22V7ydd_NyD1xLve0esoro7vJpvkZNmZr6KtZ4r8vCGFoQYUpu78Vc_H_8ROHHZCM27yf9m00xb85oG3kGwf9HzTKAvXhBMXBHhBoEI7pte6FEpE-xMCJIvIyj9pdzrLk0Ej-Szu9ztSc0ustk0YLrkGLU-mLy0)
