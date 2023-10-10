---
title: "flutter로 게임 만들기 (background)"
date: "2023-10-11 00:45:22"
tags: ["flutter", "flutter game"]
---
flutter codelab에 있는 Doodle Dash 게임을 바탕으로 위로 배경이 움직이는 배경을 만들어보기로 할겁니다.

배경이 위로 움직이게 하기 위해서는 ParallaxComponent를 extends해서 assets에 있는 이미지를 가져와 레이어로 렌더링해야합니다.



> 예제에는 HasGameRef가 with되어있지않아서 에러가 발생하니 꼭  HasGameRef를 with해주세요. <br>
Undefined name 'gameRef'.
Try correcting the name to one that is defined, or defining the name.
{: .prompt-warning }

```
class World extends ParallaxComponent<DoodleDash> with HasGameRef<DoodleDash> {
 @override
 Future<void> onLoad() async {
   parallax = await gameRef.loadParallax(
     [
       ParallaxImageData('game/background/06_Background_Solid.png'),
       ParallaxImageData('game/background/05_Background_Small_Stars.png'),
       ParallaxImageData('game/background/04_Background_Big_Stars.png'),
       ParallaxImageData('game/background/02_Background_Orbs.png'),
       ParallaxImageData('game/background/03_Background_Block_Shapes.png'),
       ParallaxImageData('game/background/01_Background_Squiggles.png'),
     ],
     fill: LayerFill.width,
     repeat: ImageRepeat.repeat,
     baseVelocity: Vector2(0, -5),
     velocityMultiplierDelta: Vector2(0, 1.2),
   );
 }
}
```

좀더 자세한 설명은 아래 사이트에서 참고하시기 바랍니다.
Flutter와 Flame을 사용한 게임 빌드 
- https://codelabs.developers.google.com/codelabs/flutter-flame-game?hl=ko#0