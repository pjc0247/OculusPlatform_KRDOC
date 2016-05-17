Oculus Platform
====

앱 생성하기
----
[오큘러스 개발자 사이트](https://dashboard.oculus.com/organization/create)에 접속합니다.<br>
단체 이름을 입력하는 화면이 표시되면 이름을 입력하고 '다음'을 클릭합니다.<br>
![org](img/create_org.png)
앱 정보를 적절히 입력하여 앱을 생성합니다.<br>
![id](img/app_id.png)
앱 생성이 완료되면 앱 정보 페이지에서 발급된 앱 아이디를 확인할 수 있습니다.

Unity 에서 연동하기
----
![unity](img/unity_setting.png)<br>
![unity](img/unity_setting2.png)<br>

```cs
using Oculus.Platform;

Core.Initialize();

Users.GetLoggedInUser().OnComplete((Message msg) => {
  var user = msg.GetUser();

  // 오큘러스의 유저 식별자
  // ex) 4412314125
  var oculusUniqueID = user.ID.ToString();
  // 오큘러스 유저 아이디
  // ex) pjc8642
  var oculusUserID = user.OculusID();
            
  StartCoroutine(LoadProfileImage(user));
});
```
```cs
public UnityEngine.UI.RawImage profileImage;

// 프로필 이미지를 로드하는 코드
IEnumerator LoadProfileImage(Oculus.Platform.Models.User user)
{
  var www = new WWW(user.ImageURL);

  yield return www;

  profileImage.texture = www.texture;            
}
```

빌드 업로드하기
----
![build](img/build.png)<br>
![build_result](img/build_result.png)<br>
![upload_build](img/upload_build.png)<br>
![build_config](img/build_config.png)<br>

앱 테스터 등록하기
----
![add_dev](img/add_dev.png)<br>
![restart](img/restart.png)<br>
![library](img/library.png)<br>
![app_info](img/app_info.png)<br>
