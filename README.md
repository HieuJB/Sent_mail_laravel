# Sent_mail_laravel

Setup ENV 
MAIL_MAILER=smtp
MAIL_HOST=smtp.googlemail.com
MAIL_PORT=465
MAIL_USERNAME=vlkh00volam14@gmail.com
MAIL_PASSWORD=nguyenhieu123
MAIL_ENCRYPTION=ssl
MAIL_FROM_ADDRESS=vlkh00volam14@gmail.com
MAIL_FROM_NAME="${APP_NAME}"

Chay lenh: php artisan make:mail Gmail
use Queueable, SerializesModels;

    public $details;

    /**
     * Create a new message instance.
     *
     * @return void
     */
    public function __construct($details)
    {
        $this->details = $details;
    }

    /**
     * Build the message.
     *
     * @return $this
     */
    public function build()
    {
        return $this->subject('Mail gửi từ trang web của Hiếu')
        ->view('emails.gmail');
    }
    
    Tạo controller
    use App\Mail\Gmail;
    use Illuminate\Support\Facades\Mail;
    public function sendgmail(){
        $details = [
            'title' => 'Mail gửi từ Trung Hieu',
            'body' => 'Cảm ơn bạn đã đăng ký thành viên.'
        ];

        Mail::to('doanngoctan281999@gmail.com')->send(new Gmail($details));
        return "Email sent";
    }
    
    
    Tạo view  
    <h1>{{ $details['title'] }}</h1>
    <p>{{ $details['body'] }}</p>
    
    Tạo router 
    Route::get('/email',[gmail_controller::class,'sendgmail']);

Truong hop up len host ma gmail tai khoan moi khong cho chay thi vao link nay https://accounts.google.com/DisplayUnlockCaptcha
Truong hop bi loi thi nhan vao day https://myaccount.google.com/lesssecureapps?pli=1&rapt=AEjHL4Np4PG1DE4bstcHf2Gj8IHCpntsqwSDa9SItLruNrSfOKKVs98EHJ6dxpnCoKD20VvoaJdk18uMFWJ8FlWztMFO4_2v6Q
