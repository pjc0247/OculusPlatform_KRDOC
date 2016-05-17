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
��ŧ���� ������ ����Ʈ�� ���带 ���ε��ϸ� ��ϵ� ������ �� �׽��͵��� ��ŧ���� ���� ���� ������ �ٿ�ε� ���� �� �ֽ��ϴ�.<br>
����Ƽ���� __PC__ �÷����� �����ϰ� �����մϴ�.
![build](img/build.png)<br>
�Ʒ��� ���� ����� ������� ��µǸ�, `Data` ������ `exe` ������ �����մϴ�.<br>
![build_result](img/build_result.png)<br>
������ ������ ��ŧ���� ������ ����Ʈ�� ���ε��մϴ�.
![upload_build](img/upload_build.png)<br>
![build_config](img/build_config.png)<br>
�ʿ信 ���� ������ ������ �Է��մϴ�.<br>
__Launch File__ �׸��� �ݵ�� ���� ���� ������ ��θ� �Է��ؾ� �մϴ�.

�� �׽��� ����ϱ�
----
���ε��� ���带 �ٿ�ε� ���� �� �ִ� �������� ����ϴ� ����� �˾ƺ��ϴ�.<br>
![add_dev](img/add_dev.png)<br>
�� ���� ���������� __Platform__ -> __Developers__ �ǿ� ���ϴ�.<br>
`Add Developers` ��ư�� Ŭ���� ���ϴ� ����� �߰��մϴ�.
![restart](img/restart.png)<br>
����� �߰��Ǹ�, �ش� ������ ��ŧ���� ���α׷��� ������ؾ��մϴ�.<br>
��ŧ���� ���α׷��� __Setting__ -> __Beta__ -> __Restart Oculus__ �� Ŭ���� ��ŧ������ ������մϴ�.
![library](img/library.png)<br>
������� �Ϸ�Ǹ� ��� __Library__ �޴��� ������ ǥ�õ˴ϴ�.<br>
���� ������ �ٿ�ε� �ް�, ��ŧ���� ���α׷����� �ٷ� �����ų �� �ֽ��ϴ�.
![app_info](img/app_info.png)<br>
���� ������ ������
