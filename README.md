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
移動量を考慮した衝突
![image](https://github.com/user-attachments/assets/8e063702-f6f7-4b2c-a58c-74246fb151a3)

### Position Based Dynamics
![image](https://github.com/user-attachments/assets/7d139b67-10d7-4dc9-841a-4ea4f4f0f68b)
サンプル: /Game/ExampleContent/Niagara/PBD/PBD
![image](https://github.com/user-attachments/assets/1d46c3a7-742c-4591-ae18-86a482644d0f)
### Recreating Volumes
https://youtu.be/31GXFW-MgQk?t=2437
サンプル?: /Game/ExampleContent/Niagara/NeighborGrid3D/StructuralSupport/StructuralSupport
![image](https://github.com/user-attachments/assets/76ca40ae-1ef2-4206-acb3-584510bdbfad)
SDFを使てtcharacterのサーフェース内部にパーティクルがめり込まない世に立体的に敷き詰めることができるっぽい？
![image](https://github.com/user-attachments/assets/b08517fb-d33f-4e21-8fb6-cda07e2f526f)
### Hierarchy
パーティクルレベルで階層構造ができるっぽい
### Constraints
https://youtu.be/31GXFW-MgQk?t=2742
親子付けに関しての説明をしている
## Swept Intersections
↑をレーザーで切り裂く表現
どのようにレーザーの衝突を検出するか
レーザーの起動から三角形をつかってやってる
このコリジョンはAPIがあるっぽい
![image](https://github.com/user-attachments/assets/1818c647-02bf-4d7b-bfba-5772e57ea56e)
### Safe Particle Distribution
パーティクルのをサーフェースに分布する際の方法の一つを紹介している
![image](https://github.com/user-attachments/assets/d4faa80f-c01c-460f-b07a-c34c719cdd0a)

## Q&A
### collision補正を複数使う理由、Niagaraの新機能、SimilationStageについて
https://youtu.be/31GXFW-MgQk?t=3259
SimilationStageは複数持てる
Grid間でデータを受け渡せる
必要なシミュレーション数は設定によって変わる。(デモのトウモロコシ人間は12回)
シミュレーションの精度を確保するために複数回行う(剛体シミュレーションと感覚は一緒っぽい)

### PBDのコリジョンはどの程度フレームレートに依存する？
https://youtu.be/31GXFW-MgQk?t=3543
依存する
パーティクルの速度が速いほどフレームレートに依存する可能性が高くなる
フレーム間で移動した距離に基づいてシミュレーションを行う

### PBDはCPUでも動く？
https://youtu.be/31GXFW-MgQk?t=3635
理論的には可能だがCPU負荷が高すぎる
グリッド関連の機能はGPU専用

### ベイクされたDistanceFieldは初期化しか設定できない？アニメーションの姿勢とかでも使える？
https://youtu.be/31GXFW-MgQk?t=3686
Recreating Volumesでのスケルタルメッシュの姿勢が変わった状態の話をしてる?
SDFとの関係がちょっと分からなかったけどパーティクルパーティクルのルートかアンカーポイントの相対位置で初期化される。（多分）
アニメーションはボーンローカルに変換してボーンのTransformをかけてやってるっぽい（スキニングの要領？）
そこからresolveかけるから完全なConstraintを実現することはできない(それはそれで有機的で面白いって言ってる)

### SimilationStageは逐次実行？一部をループバディとしてチェーン化できる(並列化できるかを聞いてる？)
https://youtu.be/31GXFW-MgQk?t=3835
各ステージは逐次実行。
それがこれを実現するために大事(おそらく各ステージの出力が次の入力になってることを示唆してる？)

### トウモロコシのコリジョンメッシュ単位で正確？単純化してる？
https://youtu.be/31GXFW-MgQk?t=3879
いつかメッシュ単位でやりたいと思ってる（でも重くなる）
そこまでいくと物理シミュレーションの領域になってくる

### 球の位置とか基づいてにジオメトリを粉砕できる？
動かしているものがメッシュパーティクルかつ単一のジオメトリならいける？
パーティクルは基本的に球として運動する

### パーティクル間のひずみに基づいてパーティクルを切り離すことはできる？
https://youtu.be/31GXFW-MgQk?t=3986
できる
近くのパーティクルをクエリ→親を定期的にチェックして働いてる力に応じて親子付けを解除するとかすればいける

### パーティクルを半透明メッシュ状のDistanceField GPU Particleと衝突させるには？
https://youtu.be/31GXFW-MgQk?t=4044
水のこと？
これは動画みたほうがいいかも
一応できそう？

### CPUシミュレーションとGPUシミュレーションどちらを使うかの判断基準は？
https://youtu.be/31GXFW-MgQk?t=4176
ニーズによる
大量のパーティクルを処理するときはやっぱGPU

### パーティクルのタイムラインとかイベントからサウンドならせる？
https://youtu.be/31GXFW-MgQk?t=4272
できたはず
Content Exampleにある

### 空間ハッシュはNiagaraの一部？それともオーバーレイ？(モジュール機能のこといってる？)
https://youtu.be/31GXFW-MgQk?t=4439
隣接グリッドは内部のデータインターフェース
グリッドは自作できる
グリッドをワールド空間に変換するのはAdvancedにサンプルがある
パラメータの簡単な説明もこの質問中にしてる
/Game/ExampleContent/Niagara/NeighborGrid3D/DynamicTransforms/DynamicGridTransforms

### グリッド関連の処理はカスタムHLSLからノードになる？
https://youtu.be/31GXFW-MgQk?t=4634
まだ。将来的にやりたい

### ボイド（鳥のシミュレーション）の計算はどのくらい？パーティクルが増えるとどのように計算が増える？
https://youtu.be/31GXFW-MgQk?t=4702
ちゃんと計算してないけどPBDの計算量はmsより下
鳥はPBDより軽いからもっとはやいはず(本当か)

### VATで大量のアニメーションを線形補完するとリソースでかすぎないか
https://youtu.be/31GXFW-MgQk?t=4741
マテリアル上では単一テクスチャでやってる(VATの説明が続く)
処理速度は大したことないけどテクスチャサイズは無視できないかも(HDRだし)
講演者がかかわったプロジェクトでは問題になったことはない

### ライトと虫のインタラクトはどうやったか
https://youtu.be/31GXFW-MgQk?t=4836

Avoid Coneモジュールを作ってそれを使った
円錐をモデル化したやつ
![image](https://github.com/user-attachments/assets/cf900635-b792-4352-af73-9d46d414b824)

### トウモロコシ人間の処理速度ついて。ゲームで使えるのか
https://youtu.be/31GXFW-MgQk?t=5136
1msかかってない
デモはレイトレ使っていて処理の大半はレンダリング負荷

### カスケードはコリジョンで衝突すると回転が止まるオプションがあったけどNiagaraにはない
https://youtu.be/31GXFW-MgQk?t=5187
あとで調べてきます

### 属性の読み取りについて、クエリの際に別のアクターのtickを使うか？(OwnerActorとか更新の影響を受けるか的なことを言ってる？)
https://youtu.be/31GXFW-MgQk?t=5232
いいえ。属性の読みとりは全部Nigaraで処理している
エミッタの依存関係の話もしてる
![image](https://github.com/user-attachments/assets/4748a8ef-0a2e-44d8-a6cb-843e2c8e5ab6)
![image](https://github.com/user-attachments/assets/4902ba0e-0efa-4d82-af6e-12c611f5bc69)
![image](https://github.com/user-attachments/assets/afdba9ad-afe0-40ed-a0a9-724c53867d85)
![image](https://github.com/user-attachments/assets/fc39c929-072d-4e85-b9ac-6cf811229961)

### BBDではパーティクルの予測位置と静止位置を照合しているのか。もしパーティクルがお互いに向かって移動していたらどうなる？(1フレーム内で交差するか)
https://youtu.be/31GXFW-MgQk?t=5350
ループの繰り返し数による
エミッタが分かれている場合は認識できない
（おそらく別々のGridでシミュレーションしているパーティクル間のインタラクトはできない）

### おすすめの教材はある？
https://youtu.be/31GXFW-MgQk?t=5484  
ここがおすすめ  
https://processing.org/  




