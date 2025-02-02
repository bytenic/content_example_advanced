https://www.youtube.com/watch?v=31GXFW-MgQk

## Niagara World Interfaces
パーティクルのSpawnサンプリングの話
- CPUのTriagnleサンプリング
- GPUのDepthサンプリング
- SDFのサンプリングの話
## Distance Field Analysis
グローバルSDFを使ったサンプリング地点の算出
以下にサンプルがあり、Avoid Distance Field Surfaces_GPUでレイマーチしている
- /Game/ExampleContent/Niagara/NeighborGrid3D/Boids
## Debug Visualizations
↑のデバッグ表示マテリアルの説明とかをしてる
## Implementation 
このSDFがAPIとして公開されてるみたい。
![image](https://github.com/user-attachments/assets/cbe2eca0-e0f6-4a9b-8feb-7129eedf3f42)

## Flocks Overview
群衆制御の概要説明
![image](https://github.com/user-attachments/assets/8a0c9aff-26e8-48e6-b8cc-ddd6de6d4fe8)

### Avoid Distance Fields Surfaces
![image](https://github.com/user-attachments/assets/449a450c-d5cd-4b85-b41c-9875e770c920)
### Spatial Hash
隣接グリッドを使って近くパーティクル(鳥の)検出の最適化ができる
![image](https://github.com/user-attachments/assets/9e7e0bd2-dd20-4ace-9c73-b46d3f2b1bb2)
### Vision
![image](https://github.com/user-attachments/assets/0960b41c-6cba-4ed3-b2e3-6ba009be6936)
Boidサンプルの説明もここでしてる
![image](https://github.com/user-attachments/assets/8d04398f-0bea-41cc-afc6-c2eb516ac3b8)
### Flight Orientation
パーティクルの旋回についての説明
![image](https://github.com/user-attachments/assets/8e75ec43-e337-4893-896b-a71537aa46d8)
### Vertex Animation Textures
鳥はVATでアニメーションしてる
- VAT自体のExample:https://www.youtube.com/watch?v=1cPRYwF-Tvg
## Swarms Overview
![image](https://github.com/user-attachments/assets/c92ea291-0974-426d-8b5c-4fffb36463ae)

## Distance Fields Traversal
大量の虫を移動シミュレーション後にSDFでサーフェース状に張り付けてる
![image](https://github.com/user-attachments/assets/36f4ebd9-6f9c-4732-8e98-b9915861b8cb)
## Static Mesh Skeletal Animation
虫の足をマテリアル上で重みづけをして動かしている？
## State Machine
Niagara内でもステートが組める話
なかなかごり押してる感じですごい
![image](https://github.com/user-attachments/assets/e7c0e047-1c14-4096-9277-8cc962b37c59)

## PBD
![image](https://github.com/user-attachments/assets/9abd69c5-5d28-433d-9460-83195f0c342b)

## Continuous Collision Detection

## Position Based Dynamics

## Recreating Volumes

## Hierarchy

## Constraints


## Swept Intersections

## Safe Particle Distribution
