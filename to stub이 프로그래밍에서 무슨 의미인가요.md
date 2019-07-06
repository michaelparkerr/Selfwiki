# to stub이 프로그래밍에서 무슨 의미인가요?

- 예를 들면 이 인용구에서 무엇을 의미하는건가요?

> 외부 API를 Integrate하는 것은 현대 웹 앱에서 거의 확약이다. 그러한 Integration을 효과적으로 테스트하기 위해서 stub it out 할 필요가 있다. 좋은 stub은 만들기 쉬어야하고 실제, 현재 API 반응에 대해 꾸준히 업데이트가 되어야한다. 이 포스트에서 우리는 외부 API에 대해 stubs를 이용하는 테스팅 전략에 대해 강조할 것이다.

-------------

# A

stub은 시스템에서 기존 의존성를 제어할 수 있는 대체물입니다. stub을 이용함으로써 당신의 코드를 의존성을 직접적으로 다루지 않고 테스트할 수 있습니다.

외부 의존성 - 기존 의존성

테스트된 당신의 코드들과 당신이 제어할 수 없는 것들과의 상호작용이 시스템에서의 객체입니다.(흔한 예로, 파일시스템, 스레드, 메모리, 시간 기타 등등)

- 예제

```c
public void Analyze(string filename)
    {
        if(filename.Length<8)
        {
            try
            {
                errorService.LogError("long file entered named:" + filename);
            }
            catch (Exception e)
            {
                mailService.SendEMail("admin@hotmail.com", "ErrorOnWebService", "someerror");
            }
        }
    }
```

당신이 **mailService.SendEMail()** 메소드를 테스트하기를 원한다면, 당신은 테스트 메소드에서 *예외*를 시뮬레이션 해봐야만 한다. 그래서 당신은 당신이 원하는 결과를 시뮬레이션하기 위해 가짜 Stub **errorService** 객체를 만들 필요가 있고, 그러면 당신의 테스트 코드는 **mailService.SendEMail()** 메소드를 테스트할 수 있다. 볼 수 있듯이 당신은 기존 의존성 객체인 **ErrorService** 클래스 객체와 또 다른 의존성 객체에서 온 결과를 시뮬레이션 할 필요가 있다.