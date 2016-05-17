Oculus Platform
====

�� �����ϱ�
----
[��ŧ���� ������ ����Ʈ](https://dashboard.oculus.com/organization/create)�� �����մϴ�.<br>
��ü �̸��� �Է��ϴ� ȭ���� ǥ�õǸ� �̸��� �Է��ϰ� '����'�� Ŭ���մϴ�.<br>
![org](img/create_org.png)
�� ������ ������ �Է��Ͽ� ���� �����մϴ�.<br>
![id](img/app_id.png)
�� ������ �Ϸ�Ǹ� �� ���� ���������� �߱޵� �� ���̵� Ȯ���� �� �ֽ��ϴ�.

Unity ���� �����ϱ�
----
![unity](img/unity_setting.png)<br>
![unity](img/unity_setting2.png)<br>

```cs
using Oculus.Platform;

Core.Initialize();

Users.GetLoggedInUser().OnComplete((Message msg) => {
  var user = msg.GetUser();

  // ��ŧ������ ���� �ĺ���
  // ex) 4412314125
  var oculusUniqueID = user.ID.ToString();
  // ��ŧ���� ���� ���̵�
  // ex) pjc8642
  var oculusUserID = user.OculusID();
            
  StartCoroutine(LoadProfileImage(user));
});
```
```cs
public UnityEngine.UI.RawImage profileImage;

// ������ �̹����� �ε��ϴ� �ڵ�
IEnumerator LoadProfileImage(Oculus.Platform.Models.User user)
{
  var www = new WWW(user.ImageURL);

  yield return www;

  profileImage.texture = www.texture;            
}
```

���� ���ε��ϱ�
----
![build](img/build.png)<br>
![build_result](img/build_result.png)<br>
![upload_build](img/upload_build.png)<br>
![build_config](img/build_config.png)<br>

�� �׽��� ����ϱ�
----
![add_dev](img/add_dev.png)<br>
![restart](img/restart.png)<br>
![library](img/library.png)<br>
![app_info](img/app_info.png)<br>