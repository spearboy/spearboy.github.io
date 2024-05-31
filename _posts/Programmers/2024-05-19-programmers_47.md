---
layout: post
title: PHPMailer를 사용해보자!
date: 2024-05-19 23:13 +0900
description: 
image:
category: [PHP, Lv2]
tags: code PHP
published: true
sitemap: true
---

# PHPMailer를 사용해보자!

안녕하세요 오늘은 제가 사용했던 php의 `PHPMailer`의 사용법을 한번 알아보겠습니다.

다운로드 링크는 [PHPMailer](https://github.com/PHPMailer/PHPMailer)입니다.

## PHPMailer?

PHPMailer는 PHP로 이메일을 전송하는 데 사용되는 오픈 소스 라이브러리입니다. 이 라이브러리는 SMTP(Simple Mail Transfer Protocol)를 통해 이메일을 쉽게 보내는 기능을 제공합니다. PHP의 기본 mail() 함수보다 더 강력하고 유연한 기능을 제공하여 이메일 전송 작업을 단순화하고 향상시켜 줍니다.

### 주요 특징

1. SMTP 지원: PHPMailer는 SMTP를 사용하여 이메일을 전송할 수 있습니다. 이는 이메일 전송의 신뢰성과 보안성을 높이는 데 도움이 됩니다.
2. HTML 이메일: HTML 형식의 이메일을 쉽게 작성하고 보낼 수 있습니다. 이를 통해 스타일링된 이메일을 만들 수 있습니다.
3. 첨부 파일: 이메일에 파일을 첨부할 수 있습니다. 여러 파일도 쉽게 첨부 가능합니다.
4. 인증 지원: SMTP 인증을 통해 보안이 강화된 이메일 전송을 할 수 있습니다.
5. 다국어 지원: 여러 언어로 오류 메시지와 알림을 제공하여 국제적인 사용이 가능합니다.
6. 디버깅: 이메일 전송 과정에서 발생하는 문제를 쉽게 추적하고 해결할 수 있도록 디버그 기능을 제공합니다.

### 사용 이유

1. 단순함: 이메일 전송을 위한 복잡한 코드를 간단하게 만들어 줍니다.
2. 유연성: 다양한 이메일 전송 옵션을 제공하여 다양한 요구사항에 맞출 수 있습니다.
3. 보안성: SMTP 인증과 같은 보안 기능을 쉽게 구현할 수 있어 보안성이 높습니다.
4. 기능성: HTML 이메일, 첨부 파일 등 고급 기능을 지원하여 다양한 이메일 형식을 보낼 수 있습니다.
5. 커뮤니티와 문서: 잘 정리된 문서와 활발한 커뮤니티가 있어 문제 해결이 용이합니다.

PHPMailer는 이러한 이유들로 인해 PHP 개발자들이 이메일 기능을 구현할 때 많이 사용하는 도구입니다.

이렇게 `PHPMailer`가 무엇인지 알아보았으니 예제 코드를 이용해 본격적으로 `PHPMailer`를 사용해보겠습니다.

## PHPMailer 예제 코드

```php
require '../PHPMailer/src/Exception.php';
require '../PHPMailer/src/PHPMailer.php';
require '../PHPMailer/src/SMTP.php';

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

// Sample data for demonstration
$userEmail = 'user@example.com';
$userName = 'John Doe';

date_default_timezone_set('Asia/Seoul');

$mail = new PHPMailer;
$mail->isSMTP(); // Set mailer to use SMTP
$mail->Host = 'smtp.server.com'; // Specify main and backup SMTP servers
$mail->Port = 465; // TCP port to connect to
$mail->SMTPSecure = 'ssl'; // Enable TLS encryption, `ssl` also accepted
$mail->SMTPAuth = true; // Enable SMTP authentication
$mail->Username = 'account'; // SMTP username
$mail->Password = 'password'; // SMTP password
$mail->setFrom('tsagaanaa123@naver.com', 'picker'); // Sender's email address and name
$mail->addReplyTo('picker@pickstom.com', 'picker'); // Reply-to address
$mail->addAddress($userEmail, $userName); // Add a recipient

$mail->Subject = 'OOO님께'; // Email subject
$mail->CharSet = 'UTF-8'; // Character set
$mail->msgHTML("<html><body>안녕하세요 저는 OOO입니다.</body></html>"); // HTML message body
$mail->AltBody = "안녕하세요 저는 OOO입니다."; // Plain text body for non-HTML email clients

if (!$mail->send()) {
  echo 'Mailer Error: ' . $mail->ErrorInfo; // Display error message if email fails to send
} else {
  echo 'Message sent successfully!'; // Display success message if email is sent
}
```

### 상세 설명

1. `PHPMailer` 포함 및 사용 선언

```php
require '../PHPMailer/src/Exception.php';
require '../PHPMailer/src/PHPMailer.php';
require '../PHPMailer/src/SMTP.php';

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;
```

`PHPMailer`를 포함하고 사용할 수 있도록 네임스페이스를 선언합니다.

2. 샘플 데이터 설정

```php
$userEmail = 'user@example.com';
$userName = 'John Doe';
$randomCode = 'ABC123';
```

이메일 전송을 테스트하기 위해 샘플 데이터를 설정합니다.

3. 타임존 설정

```php
date_default_timezone_set('Asia/Seoul');
```

PHP 스크립트의 기본 타임존을 설정합니다.

4. PHPMailer 객체 생성 및 설정

```php
$mail = new PHPMailer;
$mail->isSMTP(); // Set mailer to use SMTP
$mail->Host = 'smtp.server.com'; // Specify main and backup SMTP servers
$mail->Port = 465; // TCP port to connect to
$mail->SMTPSecure = 'ssl'; // Enable TLS encryption, `ssl` also accepted
$mail->SMTPAuth = true; // Enable SMTP authentication
$mail->Username = 'account'; // SMTP username
$mail->Password = 'password'; // SMTP password
$mail->setFrom('tsagaanaa123@naver.com', 'picker'); // Sender's email address and name
$mail->addReplyTo('picker@pickstom.com', 'picker'); // Reply-to address
$mail->addAddress($userEmail, $userName); // Add a recipient
```

- `new PHPMailer`로 `PHPMailer` 객체를 생성합니다.
- `isSMTP()`를 사용하여 `SMTP`를 사용하도록 설정합니다.
- `Host` 속성에 `SMTP` 서버 주소를 지정합니다.
- `Port` 속성에 포트 번호를 설정합니다.
- `SMTPSecure` 속성에 `SSL`을 사용하도록 설정합니다.
- `SMTPAuth` 속성에 `SMTP` 인증을 사용하도록 설정합니다.
- `Username` 및 `Password` 속성에 `SMTP` 서버의 로그인 자격 증명을 설정합니다.
- `setFrom` 메서드로 보낸 사람의 이메일 주소와 이름을 설정합니다.
- `addReplyTo` 메서드로 회신 이메일 주소를 설정합니다.
- `addAddress` 메서드로 수신자의 이메일 주소와 이름을 설정합니다.

5. 이메일 내용 설정

```php
$mail->Subject = 'OOO님께'; // Email subject
$mail->CharSet = 'UTF-8'; // Character set
$mail->msgHTML("<html><body>안녕하세요 저는 OOO입니다.</body></html>"); // HTML message body
$mail->AltBody = "안녕하세요 저는 OOO입니다."; // Plain text body for non-HTML email clients
```

- `Subject` 속성에 이메일 제목을 설정합니다.
- `CharSet` 속성에 문자 인코딩을 설정합니다.
- `msgHTML` 메서드로 `HTML` 형식의 이메일 본문을 설정합니다.
- `AltBody` 속성에 `HTML`을 지원하지 않는 클라이언트를 위한 텍스트 형식의 이메일 본문을 설정합니다.

6. 이메일 전송 및 결과 처리

```php
if (!$mail->send()) {
  echo 'Mailer Error: ' . $mail->ErrorInfo; // Display error message if email fails to send
} else {
  echo 'Message sent successfully!'; // Display success message if email is sent
}
```

- `send` 메서드를 사용하여 이메일을 전송합니다.
- 전송에 실패하면 오류 메시지를 출력하고, 성공하면 성공 메시지를 출력합니다.

이렇게 예제를 상세하게 한번 알아보았습니다.

도움이 되셨다면 댓글한번씩만 달아주세요!