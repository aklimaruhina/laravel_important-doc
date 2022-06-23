# laravel_important-doc
laravel mail function
When creating mail function for laravel we ofter forget how to send mail. Here i listed some to remember how to send mail via laravel
some file that need to change are 

.env, 
controller, 
route 
views file 
controller file: 

\Mail::send(
         'frontend.emails.send-mail', // view file name with folder name
         array( // Send data to view file as parameters 
            'name' => $request->name,
            'email' => $request->email,
            'phone' => $request->phone,
            'text' => $request->message,
         ),
         function ($message) use ($request) {
            $message->from($request->email);
            $message->to([$request->email, 'from@gmail.com'])->subject('Customer Message');
         }
      );
      
 and in view file 
 send-mail 
 {{ name }}
 will call 
 and most important for changing env file 

MAIL_MAILER=sendmail
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
 @foreach($services->chunk(2) as $service)
            <div class="row mb-4 service_ul">
                @foreach($service as $serv)
                <div class="col-md-6">
                    <h4><span style="font-family: inherit; font-weight: normal;"> <strong>{{ $serv->service_name }} </strong> </span></h4>
                    {!! $serv->description !!}
                    <p><img src="{{asset('img/safeaviation/'.$serv->image)}}" alt="Image" style="width:400px;height:300px;" /></p>
                </div>
                @endforeach
            </div>
        @endforeach   
