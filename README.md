# Lego-LMS

* It is named Lego as you can just replace any of its components easily, the design facilates the DI principle.

* It is planned that it will support both CLI and GUI and it will be easily extensebile for adding other UIs

* It is planned that it will support both SQLStorage and JSONStorage and as you might guess it will be extensible for adding other storages.

This project is still under construction but its main design ideas are ready

```mermaid
classDiagram
    direction TB

    %% UI Layer
    class UI {
        <<abstract>>
    }

    class CLI
    class GUI

    UI <|.. GUI
    UI <|.. CLI

    %% Core
    class LMS {
        -ui : UI
        -storage : Storage
        +run()
    }

    %% Storage Layer
    class Storage {
        <<abstract>>
    }

    class SQLStorage
    class JSONStorage
    class FileEngine

    Storage <|.. SQLStorage
    Storage <|.. JSONStorage

    JSONStorage --> FileEngine : owns / uses

    %% Relationships
    LMS --> UI : owns / uses
    LMS --> Storage : owns / uses
```
