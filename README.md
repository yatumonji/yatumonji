mb_language("japanese");
mb_internal_encoding("UTF-8");
require 'PHPMailer/PHPMailerAutoload.php';

$mailer = new PHPMailer();
$mailer->IsSMTP();
$mailer->Encoding = "7bit";
$mailer->CharSet = '"iso-2022-jp"';

$mailer->Host = 'smtp.gmail.com';
$mailer->Port = 587;
$mailer->SMTPAuth = TRUE;
$mailer->SMTPSecure = "tls";
$mailer->Username = 'info@hoge2.net'; // Gmailログインアドレス
$mailer->Password = 'hogehoge'; // Gmailログインパスワード

$mailer->From     = 'info@hoge2.net'; // Fromアドレス
$mailer->FromName = mb_encode_mimeheader(mb_convert_encoding("山田太郎","JIS","UTF-8"));
$mailer->Subject  = mb_encode_mimeheader(mb_convert_encoding("メールのタイトル","JIS","UTF-8"));
$mailer->Body     = mb_convert_encoding("メールの本文です","JIS","UTF-8");
$mailer->AddAddress('info@loginmylife.co.jp'); // Toアドレス

if($mailer->Send()){
	echo "送信しました";
}
else{
	echo "エラー: " . $mailer->ErrorInfo;
}
