# yii2-chat-adminlte
yii2 chat widget widget admin lte

add via composer :
<p>"sintret/yii2-chat-adminlte": "dev-master"</p>

You just add table chat to your database with this :

<pre>CREATE TABLE `chat` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `userId` INT(11) DEFAULT NULL,
  `message` TEXT,
  `updateDate` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=INNODB;
</pre>
<p>
and calling the widget in the view like this :
<?= \sintret\chat\ChatRoom::widget(['url'=>  \yii\helpers\Url::to(['/chat/send-chat'])]); ?>
</p>

<p>in your controller eg ChatController action sendChat</p>

<code>
public function actionSendChat() {
        $message = $_POST['message'];
        if ($message) {
            $model = new \sintret\chat\models\Chat;
            $model->message = $message;
            if ($model->save()) {
                echo \sintret\chat\ChatRoom::data();
            } else {
                print_r($model->getErrors());
                exit(0);
            }
        }
    }
</code>