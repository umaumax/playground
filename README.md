# playground

```diag
wdiag {
  network dmz {
      address = "210.x.x.x/24"

      web01 [address = "210.x.x.1"];
      web02 [address = "210.x.x.2"];
  }
  network internal {
      address = "172.x.x.x/24";

      web01 [address = "172.x.x.1"];
      web02 [address = "172.x.x.2"];
      db01;
      db02;
  }
}
```

```nwdiag
wdiag {
  network dmz {
      address = "210.x.x.x/24"

      web01 [address = "210.x.x.1"];
      web02 [address = "210.x.x.2"];
  }
  network internal {
      address = "172.x.x.x/24";

      web01 [address = "172.x.x.1"];
      web02 [address = "172.x.x.2"];
      db01;
      db02;
  }
}
```


```uml
@startuml

participant "local" as Local
participant "remote" as Remote

loop monitoring clipboard
    opt if local local clipboard has changed
        activate Local
        Local -> Remote: send clipboard via ssh tunnel
        note right #lightgreen: base64\nformat
        Remote -> Remote: update clipboard
    end

    opt if remote clipboard has changed
        activate Remote
        Remote -> Local: send clipboard via ssh tunnel
        note left #lightgreen: base64\nformat
        Local -> Local: update clipboard
    end

    break ctrl-c
    end
end

@enduml
```

hoge

``` dot
  digraph G {
    CoreData [shape=box]
    FLMAssetFetchService [shape=box]
    AppDelegate -> FLMAssetFetchService [label="1.start"]
    FLMAssetFetchService -> FLMAssetFetchOperation [label="2.Kick"]
    FLMAssetFetchOperation -> FLMAssetFetchService [label="3.NSNotification(FetchedAsset)"]
    FLMAssetFetchOperation -> FLMFetchedAssetTransformer [label="ALAsset or PHAsset"]
    FLMFetchedAssetTransformer -> FLMAssetFetchOperation [label=FLMFetchedAsset]
    FLMAssetFetchService -> "FLMAssetStoreOperation" [label="4.FetchedAsset"]
    "FLMAssetStoreOperation" -> CoreData [label="5.Commit FLMPhoto, FLMAlbum"]
    "FLMAssetStoreOperation" -> App [label="6.Notify via NSNotification"]
  }
```

https://raw.githubusercontent.com%2FTLmaK0%2Fgravizo%2Fmaster%2FREADME.md)
https://raw.githubusercontent.com/TLmaK0/gravizo/master/README.md

![Alt text](https://g.gravizo.com/source/custom_mark13?https%3A%2F%2Fraw.githubusercontent.com%2FTLmaK0%2Fgravizo%2Fmaster%2FREADME.md)
<details> 
<summary></summary>
custom_mark13
@startuml;
actor User;
participant "First Class" as A;
participant "Second Class" as B;
participant "Last Class" as C;
User -> A: DoWork;
activate A;
A -> B: Create Request;
activate B;
B -> C: DoWork;
activate C;
C -> B: WorkDone;
destroy C;
B -> A: Request Created;
deactivate B;
A -> User: Done;
deactivate A;
@enduml
custom_mark13
</details>
