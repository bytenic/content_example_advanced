# Advanced Particles
UE5.5.1で確認したもの

## Simulation Stage Fill Render Target,  Advect Grid 2D Collection
| /Game/ExampleContent/Niagara/Grid2D/FIllRenderTarget  | /Game/ExampleContent/Niagara/Grid2D/AdvectGrid |
| ------------- | ------------- |
| ![image](https://github.com/user-attachments/assets/1552bcaa-f362-4942-bb45-659f6d9e85c9)  | ![image](https://github.com/user-attachments/assets/678b4adf-61b8-4d06-bfe3-9e7afee3707b)  |

SimulationStageを使ってテクスチャをサンプル→RenderTargetに描画してマテリアルに転送する一連のサンプルと  
グリッドを使ってテクスチャのUVを変えたり、2Dグリッドを使ってノイズを使ったシミュレーション結果を  
RenderTargetに描画したりしている。  
Texture or Grid -> RenderTargetに書き込む処理や、シミュレーションはスクラッチパッドでやっている  
マテリアルへはAttribute Bindingを使えばいけるっぽい。  
ただ新規でSimulationStageを作ろうとしたときにエミッタプロパティ内にあるはずのEnable Simulation Stagesのチェックが見つからない  

## Communicate with External Render Targets
| /Game/ExampleContent/Niagara/Grid2D/Niagara_ExternalRenderTarget  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/cadf064b-cf25-4bc4-a21a-3279cf7d9fb7)  |

BlueprintからRenderTargetを作成してNiagaraに受け渡し→Niagaraでシミュレーションしたものを  
BPが保持している別メッシュのマテリアルのテクスチャにアサインするまでの一連のサンプル。  
何かしらのシミュレーション結果をブロードキャストしたりするときに使えるかもしれない  

## Sample GBuffer Attributes
| /Game/ExampleContent/Niagara/Gbuffer/SpawnOnGBuffer  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/c415e78c-4589-4830-a013-97c6914cc14e)  |

パーティクルのスポーン位置からGbufferのUVに変換してGBufferにアクセスするサンプル。  
CustomHLSLでサンプル位置とGbufferのDepthを比較していて、差が大きい場合はParitcleを殺している。  
パーティクルを強制的に殺すにはエンジンが提供しているAlive変数をFalseにすると良いっぽい。(スクラッチパッドからアクセスできた)  

## Skeletal Mesh Reproduction
| /Game/ExampleContent/Niagara/Meshes/SkeletalMeshes/Emitter/SkeletalMeshReproductionSystem_Demo_GPU  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/e88b79b2-c605-462f-b39e-e21b86abddf5)  |

スキンメッシュのトライングルデータを読んでパーティクルを配置して、  
ほかのエミッタのパーティクルの位置と速度に合わせてインタラクトさせるサンプル  
他エミッタAttributeの読み込みとかが参考になりそう。  
パーティクルの色付けとかはマテリアル上でやってるっぽい？  

| こうすることでほかのエミッタで共有してAtrributeを参照することができる  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/a77902f4-de64-4f4c-a16b-152783cb7c52)  |

## Distance Field Traversal
| /Game/ExampleContent/Niagara/DistanceField/InsectLight  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/71f4f3a0-1ac0-48ec-93f6-2182a22cd524) |

Niagara Advancedの動画にあった光から虫が逃げていくサンプル。  
開いたらDevice Removeが起こったので危険  

## Particle Attribute Reader
|/Game/ExampleContent/Niagara/AttributeReader/AttributeReaderSimple  /Game/ExampleContent/Niagara/AttributeReader/AttributeReaderRing|
| ------------- |
|![image](https://github.com/user-attachments/assets/a3642b9d-186b-42b1-a278-1b57113ba533)|

他のエミッタからパーティクルのAtrributeを読み取るサンプル  
以下の箇所でエミッタを指定。  
ReaderはEmitterのAttributeとしてParameterを作成できる。  
|Spawn時に他のエミッタを指定|
| ------------- |
| ![image](https://github.com/user-attachments/assets/56a83fcb-6748-43c2-aea6-11843d882de6)|

読み取りはスクラッチパッドやモジュールからできる  
|Particle Update|
| ------------- |
|![image](https://github.com/user-attachments/assets/7bf238bf-a930-4720-813a-263d9ee8bf49)|

## Follow The Leader 1.0
|/Game/ExampleContent/Niagara/AttributeReader/AttributeReaderFollow|
| ------------- |
|![image](https://github.com/user-attachments/assets/f7bd556e-ad1a-4709-bac8-d1fd95ee556e)|

赤いパーティクルに別エミッタの緑パーティクルを追従させるサンプル。  
赤のエミッタを緑のパーティクルのエミッタからAttributeReaderで読み取って  
Spawn時に追従する赤側のParticleIDとオフセットを設定して  
更新時に追従するようなスクリプトで動かしている。  

## Spawn Particles From Another Emitter
|/Game/ExampleContent/Niagara/AttributeReader/AttributeReaderStreamers|
| ------------- |
|![image](https://github.com/user-attachments/assets/c78f187c-5858-4508-8821-310d12c239e1)|

他のエミッタのパーティクルからスポーンさせるサンプル。  
まず Spawn Particles from Other Emitterからスポーンさせるパーティクル数をパラメータに応じて決定  
|(コメント翻訳)Spawn Particles From Other EmitterとSample Particles From Other Emitterはペアで動作します。  spawnモジュールは他のエミッターに新しいパーティクルを問い合わせ、  このエミッターにマッチする適切な数を生成します。|
| ------------- |
|![image](https://github.com/user-attachments/assets/7cf71631-37b7-4c39-9238-c54393442a10)|

次にSample Particle from Other Emitterからどのアトリビュートを適用するか決定。  
オリジナルの動きをつけたいときはVelocityをDisbleにして後続モジュールで動きをつけたら良さそう  
|(コメント翻訳)次にサンプルモジュールは、どのアトリビュートに注目し、どのようにアトリビュートを適用するかを決定します。  Output Onlyを選択すると、サンプリングされた値が出力値に書き込まれますが、  そのサンプリングされた値は新しくスポーンさたパーティクルには適用されません。|
| ------------- |
|![image](https://github.com/user-attachments/assets/10f8c750-98e3-459a-9207-f96fdbcf439d)|

## Iterative Constraints
| /Game/ExampleContent/Niagara/AttributeReader/Constraints/Chain_SimulationStages  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/d959b54e-320d-4a03-8dc8-246f329db883)  |

チェーンのシミュレーションを行うサンプル。  
Resolverの処理をシミュレーションステージでループさせてやってる。  
各チェーン間の読み取りはParticle Attribute ReaderをSimuilationStageで使ってやる模様。  
Resolverの処理はけっこう込み入ったスクリプトになるので実際に使うとなったときに読むでよさそう。  

## Color Copy by Cell
| /Game/ExampleContent/Niagara/NeighborGrid3D/ColorQuery  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/48e4d25e-669a-4d19-bc5f-a04ab3dca288)  |

グリッドにデータを書き込んだり読み込んだりするサンプル。  
まず複数のエミッタからグリッドの情報を読むのでSystemでグリッドを作成する。  
![image](https://github.com/user-attachments/assets/47c1d0d5-af1e-4013-8b44-7d39fb1feb4d)  


グリッドの書き込みはこのエミッタのスクラッチパッドから  
![image](https://github.com/user-attachments/assets/ab7f8443-ca92-42d5-b6df-69f0179dfc94)  
以下のHLSLで自身のパーティクルが所属しているグリッドのインデックスを書き込む。    
パーティクルのスポーン数が5で領域は8あるので、1つもパーティクルが所属していないセルも出る
```
AddedToGrid = false;

#if GPU_SIMULATION

// Derive the Neighbor Grid Index from the world position
float3 UnitPos;
NeighborGrid.SimulationToUnit(Position, SimulationToUnit, UnitPos);

int3 Index;
NeighborGrid.UnitToIndex(UnitPos, Index.x,Index.y,Index.z);

// Verify that the derived index is valid.
int3 NumCells;
NeighborGrid.GetNumCells(NumCells.x, NumCells.y, NumCells.z);

if (Index.x >= 0 && Index.x < NumCells.x && 
    Index.y >= 0 && Index.y < NumCells.y && 
	Index.z >= 0 && Index.z < NumCells.z)
{
    int LinearIndex;
    NeighborGrid.IndexToLinear(Index.x, Index.y, Index.z, LinearIndex);

    // Increment the neighbor count for this cell. This records the number of overlaps
    // and can return a higher count than the MaxNeighborsPerCell
    int PreviousNeighborCount;
    NeighborGrid.SetParticleNeighborCount(LinearIndex, 1, PreviousNeighborCount);

    int MaxNeighborsPerCell;
    NeighborGrid.MaxNeighborsPerCell(MaxNeighborsPerCell);

    // Limit the number of neighbors added to each cell
    
    if (PreviousNeighborCount < MaxNeighborsPerCell)
    {
        AddedToGrid = true;

        int NeighborGridLinear;
        NeighborGrid.NeighborGridIndexToLinear(Index.x, Index.y, Index.z, PreviousNeighborCount, NeighborGridLinear);

        int IGNORE;
        NeighborGrid.SetParticleNeighbor(NeighborGridLinear, ExecIndex, IGNORE);
    }		
}
#endif
```

グリッドの読み取りはここ。  
 
![image](https://github.com/user-attachments/assets/19bfe5d1-d00e-4a64-997c-35d9d3bd0752)  
グリッドの読み取りは以下のHLSLから読み取る。  
自分が所属しているセルにWriteEmitterで書き込みがあったパーティクルがあった場合、  
そのパーティクルの属性を読み取って色付けしている。  
パーティクルの色自体はWriteエミッタのInitialize Particleでランダムな値を入れていてそれを使っている。  
```
NeighborIndex = -1;

#if GPU_SIMULATION

bool Valid;

// Derive the Neighbor Grid Index from the world position
float3 UnitPos;
NeighborGrid.SimulationToUnit(Position, SimulationToUnit, UnitPos);

int3 Index;
NeighborGrid.UnitToIndex(UnitPos, Index.x,Index.y,Index.z);

// Initialize the closest distance to a really large number
float neighbordist =  3.4e+38;

// loop over all neighbors in this cell
int MaxNeighborsPerCell;
NeighborGrid.MaxNeighborsPerCell(MaxNeighborsPerCell);

for (int i = 0; i < MaxNeighborsPerCell; ++i)
{
    // Find the ExecIndex for the current neighbor particle
    int NeighborLinearIndex;
    NeighborGrid.NeighborGridIndexToLinear(Index.x, Index.y, Index.z, i, NeighborLinearIndex);

    int CurrNeighborIdx;
    NeighborGrid.GetParticleNeighbor(NeighborLinearIndex, CurrNeighborIdx);

    // Only proceed if the returned index is valid. This is most often triggered
    // by there being fewer neighbors in the cell than the MaxNeighborsPerCell limit.
    if (CurrNeighborIdx != -1)
    {
        // Use the Attribute Reader to query the position of the neighbor particle
        float3 NeighborPos;
        AttributeReader.GetVectorByIndex<Attribute="Position">(CurrNeighborIdx, Valid, NeighborPos);

        // Compare the distance found maintaining the closest
        const float3 delta = Position - NeighborPos;
        const float dist = length(delta);

        if( dist < neighbordist )
        {
            neighbordist = dist;
            NeighborIndex = CurrNeighborIdx;
        }
    }  
}    

#endif
```

## Dynamic Grid Transform
| /Game/ExampleContent/Niagara/NeighborGrid3D/DynamicTransforms/DynamicGridTransforms  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/78d065bb-ddc0-4ba4-a8db-05fd66f53ab9)  |

シミュレーションGridの回転サンプル。  
RotatinonMatrixはSystem上で更新、共有している  

## Max Neighbors Per Cell
| /Game/ExampleContent/Niagara/NeighborGrid3D/PropagateNeighbors  |
| ------------- |
| ![image](https://github.com/user-attachments/assets/d94c8da1-29f2-4d2d-b33a-1c2e3a612a32)  |

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
