# Advanced Particles
UE5.5.1で確認したもの

## Simulation Stage Fill Render Target,  Advect Grid 2D Collection

| /Game/ExampleContent/Niagara/Grid2D/FIllRenderTarget  | /Game/ExampleContent/Niagara/Grid2D/AdvectGrid |
| ------------- | ------------- |
| ![image](https://github.com/user-attachments/assets/1552bcaa-f362-4942-bb45-659f6d9e85c9)  | ![image](https://github.com/user-attachments/assets/678b4adf-61b8-4d06-bfe3-9e7afee3707b)  |

SimulationStageを使ってテクスチャをサンプル→RenderTargetに描画してマテリアルに転送する一連のサンプルと  
グリッドを使ってテクスチャのUVを変えたり、2Dグリッドを使ってノイズを使ったシミュレーション結果を  
RenderTargetに描画したりしている。  
マテリアルへはAttribute Bindingを使えばいけるっぽい。  
ただ新規でSimulationStageを作ろうとしたときにエミッタプロパティ内にあるはずのEnable Simulation Stagesのチェックが見つからない  

## Communicate with External Render Targets
サンプル
- /Game/ExampleContent/Niagara/Grid2D/Niagara_ExternalRenderTarget
![image](https://github.com/user-attachments/assets/cadf064b-cf25-4bc4-a21a-3279cf7d9fb7)

## Sample GBuffer Attributes
サンプル
- /Game/ExampleContent/Niagara/Gbuffer/SpawnOnGBuffer
![image](https://github.com/user-attachments/assets/c415e78c-4589-4830-a013-97c6914cc14e)

## Skeletal Mesh Reproduction
サンプル
- /Game/ExampleContent/Niagara/Meshes/SkeletalMeshes/Emitter/SkeletalMeshReproductionSystem_Demo_GPU
![image](https://github.com/user-attachments/assets/e88b79b2-c605-462f-b39e-e21b86abddf5)

## Distance Field Traversal
サンプル
- /Game/ExampleContent/Niagara/DistanceField/InsectLight
![image](https://github.com/user-attachments/assets/71f4f3a0-1ac0-48ec-93f6-2182a22cd524)

## Particle Attribute Reader
サンプル
- /Game/ExampleContent/Niagara/AttributeReader/AttributeReaderSimple
- /Game/ExampleContent/Niagara/AttributeReader/AttributeReaderRing
![image](https://github.com/user-attachments/assets/a3642b9d-186b-42b1-a278-1b57113ba533)

## Follow The Leader 1.0
サンプル
- /Game/ExampleContent/Niagara/AttributeReader/AttributeReaderFollow
![image](https://github.com/user-attachments/assets/f7bd556e-ad1a-4709-bac8-d1fd95ee556e)

## Spawn Particles From Another Emitter
サンプル
- /Game/ExampleContent/Niagara/AttributeReader/AttributeReaderStreamers
![image](https://github.com/user-attachments/assets/c78f187c-5858-4508-8821-310d12c239e1)

## Iterative Constraints
サンプル
- /Game/ExampleContent/Niagara/AttributeReader/Constraints/Chain_SimulationStages
![image](https://github.com/user-attachments/assets/d959b54e-320d-4a03-8dc8-246f329db883)

## Color Copy by Cell
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/ColorQuery  
![image](https://github.com/user-attachments/assets/48e4d25e-669a-4d19-bc5f-a04ab3dca288)

## Dynamic Grid Transform
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/DynamicTransforms/DynamicGridTransforms
![image](https://github.com/user-attachments/assets/78d065bb-ddc0-4ba4-a8db-05fd66f53ab9)

## Max Neighbors Per Cell
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/ColorQuery
- /Game/ExampleContent/Niagara/NeighborGrid3D/FollowTheLeaders
- /Game/ExampleContent/Niagara/NeighborGrid3D/PropagateNeighbors
![image](https://github.com/user-attachments/assets/d94c8da1-29f2-4d2d-b33a-1c2e3a612a32)

## Color Propagation
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/PropagateNeighbors
![image](https://github.com/user-attachments/assets/e9c512f5-bd72-49ea-8bd7-9b0f2c3f682b)

## Follow The Leader 2.0
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/FollowTheLeaders
![image](https://github.com/user-attachments/assets/1087e040-2254-4e5d-991b-2b929f8b0b65)

## Position Based Dynamics
サンプル
- /Game/ExampleContent/Niagara/PBD/PBD  
![image](https://github.com/user-attachments/assets/ce232ed4-d26f-417b-8abd-af6340f05ad2)  
PBDのサンプル  
AdvencedEffectの動画でも紹介されてる。  
詳細は動画の方を見たほうが良い  

## Plexus
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/Plexus/Plexus
![image](https://github.com/user-attachments/assets/2c6f6f90-2703-4714-9123-6513dab6cffa)

## Structural Support
サンプル  
- /Game/ExampleContent/Niagara/NeighborGrid3D/StructuralSupport/StructuralSupport
![image](https://github.com/user-attachments/assets/7df3625c-438c-431f-9f72-2185c5aa1912)  
PBDのサンプル  
AdvencedEffectの動画でも紹介されてる。  
パーティクルに親子関係やConstraintをつけたり、Surface内部のSDFをサンプルしてパーティクルを操作することで  
でAdvencedEffectのトウモロコシ人間は作られているようでそういったものを作りたいときに参考にできそう。  
詳細は動画の方を見たほうが良い  

## Boids
サンプル
- /Game/ExampleContent/Niagara/NeighborGrid3D/Boids
![image](https://github.com/user-attachments/assets/05704f91-3748-4655-946f-35eed67f7e19)   
群衆のサンプル  
AdvencedEffectの動画でも紹介されてる。  
SDFとの一番近い距離をライン描画しているサンプルなので、SDF使っていろいろするときにみると良いかも

## Component Renderer
基本的に実験的機能だったりパフォーマンスに問題があると公言されていたりするので使用しないほうが賢明  
![image](https://github.com/user-attachments/assets/6d947725-2ade-4b10-aef2-25e26a626063)

## Export Particle Data to Blueprint
サンプル
- /Game/ExampleContent/Niagara/ExportParticleData/ExportParticleData_System
- /Game/ExampleContent/Niagara/ExportParticleData/ExportParticleDataExample
![image](https://github.com/user-attachments/assets/30e77ccb-1e2d-4687-a674-6fdc8f0ac28c)

## Bind Niagara Curves to Sprite Materials
![image](https://github.com/user-attachments/assets/d9165e5d-2606-4756-bafd-70ae4c099170)  
カラーカーブをNiagaraに埋め込む機能。  
他のアセット間での取り回しができないのと、カーブ自体はNigaraSystem内部に組み込まれるはず  
（有り無しでNiagaraSystemのアセットサイズがかわった）  
正直マテリアル側で設定したほうがよさそうではある。  
また、Attribute Bindingは内部的にMaterial Dynamic Instanceを使っているので    
その分通常のマテリアルインスタンスよりオーバーヘッドがかかる。  

## Collisions in Simulation Stages
サンプル
- /Game/ExampleContent/Niagara/Collision/ParticleUpdateCollisions
- /Game/ExampleContent/Niagara/Collision/SimpleCollision_System
- /Game/ExampleContent/Niagara/Collision/SimStageCollisions
![image](https://github.com/user-attachments/assets/303e9be4-3131-4e8c-9e3d-9953a1a47e2b)

## Dynamic Distance Fields
サンプル
- /Game/ExampleContent/Niagara/DistanceField/DynamicDistanceFields/DynamicDistanceField
![image](https://github.com/user-attachments/assets/f4724721-3a4f-4b75-bd74-e0f7eb0fbaf7)
