# A.7 Expressions များ

Expression အော်ပရေတာများ၏ ဦးစားပေးအဆင့်သည် ဤအပိုင်း၏ အဓိကအပိုင်းခွဲများ၏ အစဉ်လိုက်နှင့် တူညီပြီး၊ အမြင့်ဆုံး ဦးစားပေးမှု အရင်ရှိပါသည်။ ထို့ကြောင့်၊ ဥပမာအားဖြင့်၊ + ၏ operands အဖြစ် ရည်ညွှန်းထားသော expressions များ (Par.A.7.7) သည် Pars.A.7.1-A.7.6 တွင် သတ်မှတ်ထားသော ထို expressions များဖြစ်ပါသည်။ တစ်ခုစီသော အပိုင်းခွဲတွင်၊ အော်ပရေတာများတွင် ဦးစားပေးအဆင့်တူရှိပါသည်။ ဘယ်မှညာ သို့မဟုတ် ညာမှဘယ် ပေါင်းစပ်နိုင်မှုကို ထိုနေရာတွင် ဆွေးနွေးထားသော အော်ပရေတာများအတွက် တစ်ခုစီသော အပိုင်းခွဲတွင် သတ်မှတ်ထားပါသည်။ Par.13 တွင် ပေးထားသော သဒ္ဒါသည် အော်ပရေတာများ၏ ဦးစားပေးအဆင့်နှင့် ပေါင်းစပ်နိုင်မှုကို ပေါင်းစပ်ထားပါသည်။

အော်ပရေတာများ၏ ဦးစားပေးအဆင့်နှင့် ပေါင်းစပ်နိုင်မှုကို အပြည့်အဝ သတ်မှတ်ထားပြီး၊ သို့သော် expressions များ၏ တန်ဖိုးတွက်ချက်မှု၏ အစဉ်သည်၊ အချို့ခြွင်းချက်များဖြင့်၊ သတ်မှတ်မထားပါ၊ subexpressions များတွင် side effects များ ပါဝင်သော်လည်းပင်။ ဆိုလိုသည်မှာ၊ အော်ပရေတာ၏ အဓိပ္ပါယ်ဖွင့်ဆိုချက်က ၎င်း၏ operands များကို သီးခြား အစဉ်လိုက်ဖြင့် တန်ဖိုးတွက်ချက်ကြောင်း အာမခံခြင်း မရှိလျှင်၊ implementation သည် operands များကို မည်သည့်အစဉ်ဖြင့်မဆို တန်ဖိုးတွက်ချက်ရန် လွတ်လပ်ပြီး၊ ၎င်းတို့၏ တန်ဖိုးတွက်ချက်မှုကို ရောနှောနိုင်ပါသည်။ သို့သော်၊ အော်ပရေတာတစ်ခုစီသည် ၎င်း၏ operands များက ထုတ်လုပ်သော တန်ဖိုးများကို ၎င်း ပေါ်လာသော expression ၏ parsing နှင့် လိုက်ဖက်သော နည်းဖြင့် ပေါင်းစပ်ပါသည်။

ဤစည်းမျဉ်းသည် သင်္ချာအရ commutative နှင့် associative ဖြစ်သော်လည်း computationally associative မဖြစ်နိုင်သော အော်ပရေတာများဖြင့် expressions များကို ပြန်စီစဉ်သည့် ယခင်လွတ်လပ်ခွင့်ကို ရုပ်သိမ်းပါသည်။ ဤပြောင်းလဲမှုသည် ၎င်းတို့၏ တိကျမှု၏ ကန့်သတ်ချက်များနှင့် နီးစပ်သော floating-point တွက်ချက်မှုများနှင့် overflow ဖြစ်နိုင်သည့် အခြေအနေများကိုသာ ထိခိုက်ပါသည်။

Expression တန်ဖိုးတွက်ချက်မှုတွင် overflow၊ divide check၊ နှင့် အခြားခြွင်းချက်များ၏ ကိုင်တွယ်မှုကို ဘာသာစကားက သတ်မှတ်မထားပါ။ C ၏ လက်ရှိ implementations အများစုသည် signed integral expressions များနှင့် assignments များ၏ တန်ဖိုးတွက်ချက်မှုတွင် overflow ကို လျစ်လျူရှုပါသည်၊ သို့သော် ဤအပြုအမူကို အာမခံမထားပါ။ 0 ဖြင့်စားခြင်းနှင့် floating-point ခြွင်းချက်အားလုံး၏ ကိုင်တွယ်မှုသည် implementations များကြား ကွဲပြားပြီး၊ တစ်ခါတစ်ရံ ၎င်းကို စံချိန်စံညွှန်းမဟုတ်သော library function ဖြင့် ချိန်ညှိနိုင်ပါသည်။

## A.7.1 Pointer Conversion

အကယ်၍ expression သို့မဟုတ် subexpression ၏ အမျိုးအစားသည် အချို့အမျိုးအစား T အတွက် "array of T" ဖြစ်လျှင်၊ expression ၏ တန်ဖိုးသည် array ရှိ ပထမ object သို့ pointer တစ်ခုဖြစ်ပြီး၊ expression ၏ အမျိုးအစားကို "pointer to T" သို့ ပြောင်းလဲပါသည်။ အကယ်၍ expression သည် unary & အော်ပရေတာ၏ operand တွင် သို့မဟုတ် ++၊ --၊ sizeof တွင် သို့မဟုတ် assignment အော်ပရေတာ သို့မဟုတ် . အော်ပရေတာ၏ ဘယ်ဘက် operand အဖြစ် ရှိလျှင် ဤပြောင်းလဲမှု မဖြစ်ပါ။ အလားတူပင်၊ & အော်ပရေတာ၏ operand အဖြစ် အသုံးပြုသည့်အခါမှလွဲ၍ "function returning T" အမျိုးအစား၏ expression ကို "pointer to function returning T" သို့ ပြောင်းလဲပါသည်။

## A.7.2 Primary Expressions

Primary expressions များသည် identifiers၊ constants၊ strings သို့မဟုတ် ကွင်းစကွင်းပိတ်အတွင်း expressions များဖြစ်ပါသည်။

primary-expression: identifier constant string (expression)

Identifier သည် primary expression တစ်ခုဖြစ်ပြီး၊ အောက်တွင် ဆွေးနွေးထားသည့်အတိုင်း သင့်လျော်စွာ ကြေညာထားရမည်။ ၎င်း၏ အမျိုးအစားကို ၎င်း၏ ကြေညာချက်က သတ်မှတ်ပါသည်။ Identifier သည် object တစ်ခုကို (Par.A.5) ရည်ညွှန်းလျှင် နှင့် ၎င်း၏ အမျိုးအစားသည် arithmetic၊ structure၊ union သို့မဟုတ် pointer ဖြစ်လျှင် lvalue ဖြစ်ပါသည်။

Constant သည် primary expression တစ်ခုဖြစ်ပါသည်။ ၎င်း၏ အမျိုးအစားသည် Par.A.2.5 တွင် ဆွေးနွေးထားသည့်အတိုင်း ၎င်း၏ပုံစံပေါ် မူတည်ပါသည်။

String literal သည် primary expression တစ်ခုဖြစ်ပါသည်။ ၎င်း၏ အမျိုးအစားသည် မူလက "array of char" (wide-char strings များအတွက်၊ "array of wchar_t") ဖြစ်သော်လည်း၊ Par.A.7.1 တွင် ပေးထားသော စည်းမျဉ်းကို လိုက်နာ၍၊ များသောအားဖြင့် "pointer to char" (wchar_t) သို့ ပြုပြင်ပြီး ရလဒ်သည် string ရှိ ပထမအက္ခရာသို့ pointer တစ်ခုဖြစ်ပါသည်။ ပြောင်းလဲမှုသည် အချို့ initializers များတွင်လည်း မဖြစ်ပါ၊ Par.A.8.7 ကို ကြည့်ပါ။

ကွင်းစကွင်းပိတ်ထားသော expression သည် primary expression တစ်ခုဖြစ်ပြီး ၎င်း၏ အမျိုးအစားနှင့် တန်ဖိုးသည် အလှဆင်မထားသော expression နှင့် ထပ်တူဖြစ်ပါသည်။ ကွင်းစကွင်းပိတ်များ၏ ဦးစားပေးအဆင့်သည် expression သည် lvalue ဖြစ်မဖြစ်ကို မထိခိုက်ပါ။

## A.7.3 Postfix Expressions

Postfix expressions များရှိ အော်ပရေတာများသည် ဘယ်မှညာ အုပ်စုဖွဲ့ပါသည်။

postfix-expression: primary-expression postfix-expression[expression] postfix-expression(argument-expression-listopt) postfix-expression.identifier postfix-expression->identifier postfix-expression++ postfix-expression--

argument-expression-list: assignment-expression assignment-expression-list , assignment-expression

### A.7.3.1 Array References

နောက်တွင် စတုရန်းကွင်းများအတွင်း expression တစ်ခု ပါသော postfix expression သည် subscripted array reference ကို ညွှန်ပြသော postfix expression တစ်ခုဖြစ်ပါသည်။ expressions နှစ်ခုထဲမှ တစ်ခုတွင် "pointer to T" အမျိုးအစားရှိရမည်၊ T သည် အချို့အမျိုးအစား ဖြစ်ပြီး၊ အခြားတစ်ခုတွင် integral အမျိုးအစားရှိရမည်၊ subscript expression ၏ အမျိုးအစားသည် T ဖြစ်ပါသည်။ Expression E1[E2] သည် (အဓိပ္ပါယ်ဖွင့်ဆိုချက်အရ) *((E1)+(E2)) နှင့် ထပ်တူဖြစ်ပါသည်။ နောက်ထပ် ဆွေးနွေးချက်အတွက် Par.A.8.6.2 ကို ကြည့်ပါ။

### A.7.3.2 Function Calls

Function call သည် postfix expression တစ်ခုဖြစ်ပြီး function designator ဟုခေါ်ပြီး၊ နောက်တွင် ကွင်းစကွင်းပိတ်များပါ၍ ဖြစ်နိုင်သော အလွတ်၊ ကော်မာဖြင့်ပိုင်းခြားထားသော assignment expressions များ (Par.A7.17) ၏ စာရင်းပါရှိပြီး၊ ၎င်းတို့သည် function သို့ arguments များဖြစ်ပါသည်။ အကယ်၍ postfix expression သည် လက်ရှိ scope တွင် ကြေညာချက်မရှိသော identifier ဖြင့် ဖွဲ့စည်းထားလျှင်၊ identifier ကို သွယ်ဝိုက်၍ ကြေညာပြီး ကြေညာချက်

extern int identifier();

function call ပါသော အတွင်းဆုံး block တွင် ပေးထားသကဲ့သို့ ဖြစ်ပါသည်။ Postfix expression (ဖြစ်နိုင်သော တိကျသော ကြေညာချက်နှင့် pointer ထုတ်လုပ်မှု၊ Par.A7.1 နောက်) သည် အချို့အမျိုးအစား T အတွက် "pointer to function returning T" အမျိုးအစားရှိရမည်၊ function call ၏ တန်ဖိုးတွင် T အမျိုးအစားရှိပါသည်။

ပထမထုတ်ဝေမှုတွင်၊ အမျိုးအစားကို "function" သို့ ကန့်သတ်ထားပြီး functions များသို့ pointers များမှတဆင့် ခေါ်ဆိုရန် တိကျသော * အော်ပရေတာ လိုအပ်ခဲ့ပါသည်။ ANSI စံချိန်စံညွှန်းသည် functions များနှင့် pointers များက သတ်မှတ်ထားသော functions များသို့ ခေါ်ဆိုရန် အတွက် တူညီသော syntax ကို ခွင့်ပြုခြင်းဖြင့် လက်ရှိ compilers အချို့၏ အလေ့အကျင့်ကို အတည်ပြုပါသည်။ ယခင် syntax ကို ဆက်လက်အသုံးပြုနိုင်ပါသည်။

Argument ဟူသော အသုံးအနှုန်းကို function call က ပေးပို့သော expression အတွက် အသုံးပြုပါသည်၊ parameter ဟူသော အသုံးအနှုန်းကို function အဓိပ္ပါယ်ဖွင့်ဆိုချက်က လက်ခံသော (သို့မဟုတ် ၎င်း၏ identifier) input object အတွက် သို့မဟုတ် function ကြေညာချက်တွင် ဖော်ပြထားသော အရာအတွက် အသုံးပြုပါသည်။ "actual argument (parameter)" နှင့် "formal argument (parameter)" ဟူသော အသုံးအနှုန်းများကို တစ်ခါတစ်ရံ အလားတူ ခွဲခြားမှုအတွက် အသုံးပြုပါသည်။

Function သို့ ခေါ်ဆိုရန် ပြင်ဆင်ရာတွင်၊ argument တစ်ခုစီ၏ မိတ္တူတစ်ခု ပြုလုပ်ပါသည်၊ argument-passing အားလုံးသည် တန်ဖိုးဖြင့်သာ တင်းကျပ်စွာ ဖြစ်ပါသည်။ Function သည် ၎င်း၏ parameter objects များ၏ တန်ဖိုးများကို ပြောင်းလဲနိုင်ပြီး၊ ၎င်းတို့သည် argument expressions များ၏ မိတ္တူများဖြစ်သော်လည်း၊ ဤပြောင်းလဲမှုများသည် arguments များ၏ တန်ဖိုးများကို မထိခိုက်နိုင်ပါ။ သို့သော်၊ function သည် pointer က ညွှန်ပြနေသော object ၏ တန်ဖိုးကို ပြောင်းလဲနိုင်သည်ဟု နားလည်၍ pointer တစ်ခုကို ပေးပို့နိုင်ပါသည်။

Functions များကို ကြေညာနိုင်သည့် ပုံစံနှစ်မျိုးရှိပါသည်။ ပုံစံအသစ်တွင်၊ parameters များ၏ အမျိုးအစားများသည် တိကျပြီး function ၏ အမျိုးအစား၏ အစိတ်အပိုင်းဖြစ်ပါသည်၊ ထိုကဲ့သို့သော ကြေညာချက်ကို function prototype လည်းခေါ်ပါသည်။ ပုံစံဟောင်းတွင်၊ parameter အမျိုးအစားများကို မသတ်မှတ်ပါ။ Function ကြေညာချက်ကို Pars.A.8.6.3 နှင့် A.10.1 တွင် ထုတ်ပြန်ထားပါသည်။

အကယ်၍ ခေါ်ဆိုမှုအတွက် scope တွင်ရှိသော function ကြေညာချက်သည် ပုံစံဟောင်းဖြစ်လျှင်၊ default argument promotion ကို argument တစ်ခုစီအတွက် အောက်ပါအတိုင်း အသုံးပြုပါသည် - integral promotion (Par.A.6.1) ကို integral အမျိုးအစား၏ argument တစ်ခုစီအတွက် လုပ်ဆောင်ပြီး၊ float argument တစ်ခုစီကို double သို့ ပြောင်းလဲပါသည်။ အကယ်၍ arguments များ၏ အရေအတွက်သည် function ၏ အဓိပ္ပါယ်ဖွင့်ဆိုချက်ရှိ parameters များ၏ အရေအတွက်နှင့် မညီလျှင် သို့မဟုတ် promotion နောက် argument ၏ အမျိုးအစားသည် သက်ဆိုင်ရာ parameter နှင့် မညီလျှင် ခေါ်ဆိုမှု၏ အကျိုးသက်ရောက်မှုကို သတ်မှတ်မထားပါ။ အမျိုးအစား သဘောတူညီမှုသည် function ၏ အဓိပ္ပါယ်ဖွင့်ဆိုချက်သည် ပုံစံအသစ် သို့မဟုတ် ပုံစံဟောင်း ဖြစ်ခြင်းပေါ် မူတည်ပါသည်။ အကယ်၍ ပုံစံဟောင်းဖြစ်လျှင်၊ နှိုင်းယှဉ်မှုသည် ခေါ်ဆိုမှု၏ arguments များ၏ promoted အမျိုးအစားနှင့် parameter ၏ promoted အမျိုးအစားကြားဖြစ်ပြီး၊ အကယ်၍ အဓိပ္ပါယ်ဖွင့်ဆိုချက်သည် ပုံစံအသစ်ဖြစ်လျှင်၊ argument ၏ promoted အမျိုးအစားသည် promotion မပါဘဲ parameter ကိုယ်တိုင်နှင့် ဖြစ်ရမည်။

အကယ်၍ ခေါ်ဆိုမှုအတွက် scope တွင်ရှိသော function ကြေညာချက်သည် ပုံစံအသစ်ဖြစ်လျှင်၊ arguments များကို assignment ဖြင့်ကဲ့သို့ function ၏ prototype ၏ သက်ဆိုင်ရာ parameters များ၏ အမျိုးအစားများသို့ ပြောင်းလဲပါသည်။ Arguments များ၏ အရေအတွက်သည် တိကျစွာ ဖော်ပြထားသော parameters များ၏ အရေအတွက်နှင့် တူရမည်၊ ကြေညာချက်၏ parameter စာရင်းသည် ellipsis notation (, ...) ဖြင့် အဆုံးသတ်ခြင်း မရှိလျှင်။ ထိုကိစ္စတွင်၊ arguments များ၏ အရေအတွက်သည် parameters များ၏ အရေအတွက်နှင့် ညီရမည် သို့မဟုတ် ကျော်လွန်ရမည်၊ တိကျစွာ အမျိုးအစားသတ်မှတ်ထားသော parameters များထက် ကျော်လွန်သော နောက်ဆက်တွဲ arguments များသည် အထက်အပိုဒ်တွင် ဖော်ပြထားသည့်အတိုင်း default argument promotion ခံရပါသည်။ အကယ်၍ function ၏ အဓိပ္ပါယ်ဖွင့်ဆိုချက်သည် ပုံစံဟောင်းဖြစ်လျှင်၊ အဓိပ္ပါယ်ဖွင့်ဆိုချက်ရှိ parameter တစ်ခုစီ၏ အမျိုးအစားသည် အဓိပ္ပါယ်ဖွင့်ဆိုချက် parameter ၏ အမျိုးအစားက argument promotion ခံရပြီးနောက် ဖြစ်ပါသည်။

ဤစည်းမျဉ်းများသည် အထူးရှုပ်ထွေးပါသည် အဘယ်ကြောင့်ဆိုသော် ၎င်းတို့သည် ပုံစံဟောင်းနှင့် ပုံစံအသစ် functions များ၏ ရောနှောမှုကို ထောက်ပံ့ပေးရမည့်ကြောင့်ဖြစ်ပါသည်။ ဖြစ်နိုင်လျှင် ရောနှောမှုများကို ရှောင်ကြဉ်သင့်ပါသည်။

Arguments များ၏ တန်ဖိုးတွက်ချက်မှု၏ အစဉ်ကို သတ်မှတ်မထားပါ၊ compilers များစွာ ကွဲပြားသည်ကို သတိပြုပါ။ သို့သော်၊ arguments များနှင့် function designator ကို side effects အားလုံး အပါအဝင် function ထဲ မဝင်မီ အပြည့်အဝ တန်ဖိုးတွက်ချက်ပါသည်။ မည်သည့် function သို့မဆို Recursive calls များကို ခွင့်ပြုပါသည်။

### A.7.3.3 Structure References

နောက်တွင် အစက်တစ်ခု၊ နောက်တွင် identifier တစ်ခု ပါသော postfix expression သည် postfix expression တစ်ခုဖြစ်ပါသည်။ ပထမ operand expression သည် structure သို့မဟုတ် union တစ်ခုဖြစ်ရမည်၊ identifier သည် structure သို့မဟုတ် union ၏ member တစ်ခုကို အမည်ပေးရမည်။ တန်ဖိုးသည် structure သို့မဟုတ် union ၏ အမည်ရှိသော member ဖြစ်ပြီး၊ ၎င်း၏ အမျိုးအစားသည် member ၏ အမျိုးအစားဖြစ်ပါသည်။ Expression သည် ပထမ expression က lvalue ဖြစ်လျှင် lvalue ဖြစ်ပြီး၊ ဒုတိယ expression ၏ အမျိုးအစားသည် array အမျိုးအစားမဟုတ်လျှင်။

နောက်တွင် မြှား (-နှင့် > မှ တည်ဆောက်ထားသော)၊ နောက်တွင် identifier တစ်ခု ပါသော postfix expression သည် postfix expression တစ်ခုဖြစ်ပါသည်။ ပထမ operand expression သည် structure သို့မဟုတ် union သို့ pointer တစ်ခုဖြစ်ရမည်၊ identifier သည် structure သို့မဟုတ် union ၏ member တစ်ခုကို အမည်ပေးရမည်။ ရလဒ်သည် pointer expression က ညွှန်ပြနေသော structure သို့မဟုတ် union ၏ အမည်ရှိသော member ကို ရည်ညွှန်းပြီး၊ အမျိုးအစားသည် member ၏ အမျိုးအစားဖြစ်ပါသည်၊ အကယ်၍ အမျိုးအစားသည် array အမျိုးအစားမဟုတ်လျှင် ရလဒ်သည် lvalue ဖြစ်ပါသည်။

ထို့ကြောင့် expression E1->MOS သည် (*E1).MOS နှင့် တူညီပါသည်။ Structures များနှင့် unions များကို Par.A.8.3 တွင် ဆွေးနွေးထားပါသည်။

ဤစာအုပ်၏ ပထမထုတ်ဝေမှုတွင်၊ ထိုကဲ့သို့သော expression ရှိ member အမည်သည် postfix expression တွင် ဖော်ပြထားသော structure သို့မဟုတ် union နှင့် ဆက်စပ်ရမည်ဟု စည်းမျဉ်းဖြစ်နေပြီး ဖြစ်သည်၊ သို့သော်၊ မှတ်ချက်တစ်ခုက ဤစည်းမျဉ်းကို တင်းကျပ်စွာ မအကောင်အထည်ဖော်ကြောင်း ဝန်ခံခဲ့ပါသည်။ လတ်တလော compilers များနှင့် ANSI သည် ၎င်းကို အကောင်အထည်ဖော်ပါသည်။

### A.7.3.4 Postfix Incrementation

နောက်တွင် ++ သို့မဟုတ် -- အော်ပရေတာ ပါသော postfix expression သည် postfix expression တစ်ခုဖြစ်ပါသည်။ Expression ၏ တန်ဖိုးသည် operand ၏ တန်ဖိုးဖြစ်ပါသည်။ တန်ဖိုးကို မှတ်သားပြီးနောက်၊ operand ကို ++ ဖြင့် တိုးပေးခြင်း သို့မဟုတ် -- ဖြင့် 1 ဖြင့် လျှော့ပေးခြင်း ဖြစ်ပါသည်။ Operand သည် lvalue ဖြစ်ရမည်၊ operand ပေါ်တွင် နောက်ထပ် ကန့်သတ်ချက်များနှင့် လုပ်ဆောင်မှု၏ အသေးစိတ်အတွက် additive အော်ပရေတာများ (Par.A.7.7) နှင့် assignment (Par.A.7.17) ၏ ဆွေးနွေးချက်ကို ကြည့်ပါ။ ရလဒ်သည် lvalue မဟုတ်ပါ။

## A.7.4 Unary Operators

Unary အော်ပရေတာများပါသော Expressions များသည် ညာမှဘယ် အုပ်စုဖွဲ့ပါသည်။

unary-expression: postfix expression ++unary expression --unary expression unary-operator cast-expression sizeof unary-expression sizeof(type-name)

unary operator: one of & * + - ~ !

### A.7.4.1 Prefix Incrementation Operators

++ သို့မဟုတ် -- အော်ပရေတာ နောက်က unary expression သည် unary expression တစ်ခုဖြစ်ပါသည်။ Operand ကို ++ ဖြင့် တိုးပေးခြင်း သို့မဟုတ် -- ဖြင့် 1 ဖြင့် လျှော့ပေးခြင်း ဖြစ်ပါသည်။ Expression ၏ တန်ဖိုးသည် တိုးပေးခြင်း (လျှော့ပေးခြင်း) နောက်က တန်ဖိုးဖြစ်ပါသည်။ Operand သည် lvalue ဖြစ်ရမည်၊ operands ပေါ်တွင် နောက်ထပ် ကန့်သတ်ချက်များနှင့် လုပ်ဆောင်မှု၏ အသေးစိတ်အတွက် additive အော်ပရေတာများ (Par.A.7.7) နှင့် assignment (Par.A.7.17) ၏ ဆွေးနွေးချက်ကို ကြည့်ပါ။ ရလဒ်သည် lvalue မဟုတ်ပါ။

### A.7.4.2 Address Operator

Unary အော်ပရေတာ & သည် ၎င်း၏ operand ၏ လိပ်စာကို ယူပါသည်။ Operand သည် bit-field သို့မဟုတ် register အဖြစ် ကြေညာထားသော object ကို ရည်ညွှန်းခြင်းမရှိသော lvalue ဖြစ်ရမည် သို့မဟုတ် function အမျိုးအစား ဖြစ်ရမည်။ ရလဒ်သည် lvalue က ရည်ညွှန်းသော object သို့မဟုတ် function သို့ pointer တစ်ခုဖြစ်ပါသည်။ အကယ်၍ operand ၏ အမျိုးအစားသည် T ဖြစ်လျှင်၊ ရလဒ်၏ အမျိုးအစားသည် "pointer to T" ဖြစ်ပါသည်။

### A.7.4.3 Indirection Operator

Unary * အော်ပရေတာသည် indirection ကို ညွှန်ပြပြီး၊ ၎င်း၏ operand က ညွှန်ပြနေသော object သို့မဟုတ် function ကို ပြန်ပို့ပါသည်။ အကယ်၍ operand သည် arithmetic၊ structure၊ union သို့မဟုတ် pointer အမျိုးအစား၏ object သို့ pointer တစ်ခုဖြစ်လျှင် ၎င်းသည် lvalue ဖြစ်ပါသည်။ အကယ်၍ expression ၏ အမျိုးအစားသည် "pointer to T" ဖြစ်လျှင်၊ ရလဒ်၏ အမျိုးအစားသည် T ဖြစ်ပါသည်။

### A.7.4.4 Unary Plus Operator

Unary + အော်ပရေတာ၏ operand တွင် arithmetic အမျိုးအစားရှိရမည်၊ ရလဒ်သည် operand ၏ တန်ဖိုးဖြစ်ပါသည်။ Integral operand သည် integral promotion ခံရပါသည်။ ရလဒ်၏ အမျိုးအစားသည် promoted operand ၏ အမျိုးအစားဖြစ်ပါသည်။

Unary + သည် ANSI စံချိန်စံညွှန်းနှင့်အတူ အသစ်ဖြစ်ပါသည်။ ၎င်းကို unary - နှင့် အမျှ ထည့်သွင်းခဲ့ခြင်းဖြစ်ပါသည်။

### A.7.4.5 Unary Minus Operator

Unary - အော်ပရေတာ၏ operand တွင် arithmetic အမျိုးအစားရှိရမည်၊ ရလဒ်သည် ၎င်း၏ operand ၏ အနုတ်ဖြစ်ပါသည်။ Integral operand သည် integral promotion ခံရပါသည်။ Unsigned ပမာဏ၏ အနုတ်ကို promoted အမျိုးအစား၏ အကြီးဆုံးတန်ဖိုးမှ promoted တန်ဖိုးကို နုတ်၍ တစ်ခု ပေါင်း၍ တွက်ချက်ပါသည်၊ သို့သော် အနုတ်သုညသည် သုညဖြစ်ပါသည်။ ရလဒ်၏ အမျိုးအစားသည် promoted operand ၏ အမျိုးအစားဖြစ်ပါသည်။

### A.7.4.6 One's Complement Operator

~ အော်ပရေတာ၏ operand တွင် integral အမျိုးအစားရှိရမည်၊ ရလဒ်သည် ၎င်း၏ operand ၏ one's complement ဖြစ်ပါသည်။ Integral promotions များကို လုပ်ဆောင်ပါသည်။ အကယ်၍ operand သည် unsigned ဖြစ်လျှင်၊ promoted အမျိုးအစား၏ အကြီးဆုံးတန်ဖိုးမှ တန်ဖိုးကို နုတ်၍ ရလဒ်ကို တွက်ချက်ပါသည်။ အကယ်၍ operand သည် signed ဖြစ်လျှင်၊ promoted operand ကို သက်ဆိုင်ရာ unsigned အမျိုးအစားသို့ ပြောင်းလဲ၍၊ ~ ကို အသုံးပြု၍၊ signed အမျိုးအစားသို့ ပြန်ပြောင်းခြင်းဖြင့် ရလဒ်ကို တွက်ချက်ပါသည်။ ရလဒ်၏ အမျိုးအစားသည် promoted operand ၏ အမျိုးအစားဖြစ်ပါသည်။

### A.7.4.7 Logical Negation Operator

! အော်ပရေတာ၏ operand တွင် arithmetic အမျိုးအစားရှိရမည် သို့မဟုတ် pointer ဖြစ်ရမည်၊ အကယ်၍ ၎င်း၏ operand ၏ တန်ဖိုးသည် 0 နှင့် နှိုင်းယှဉ်၍ ညီလျှင် ရလဒ်သည် 1 ဖြစ်ပြီး၊ မဟုတ်လျှင် 0 ဖြစ်ပါသည်။ ရလဒ်၏ အမျိုးအစားသည် int ဖြစ်ပါသည်။

### A.7.4.8 Sizeof Operator

sizeof အော်ပရေတာသည် ၎င်း၏ operand ၏ အမျိုးအစား၏ object တစ်ခုကို သိမ်းဆည်းရန် လိုအပ်သော bytes အရေအတွက်ကို ထုတ်ပေးပါသည်။ Operand သည် တန်ဖိုးမတွက်ချက်သော expression သို့မဟုတ် ကွင်းစကွင်းပိတ်ထားသော type name တစ်ခုဖြစ်ပါသည်။ sizeof ကို char သို့ အသုံးပြုသောအခါ၊ ရလဒ်သည် 1 ဖြစ်ပါသည်၊ array သို့ အသုံးပြုသောအခါ၊ ရလဒ်သည် array ရှိ bytes စုစုပေါင်းအရေအတွက်ဖြစ်ပါသည်။ Structure သို့မဟုတ် union သို့ အသုံးပြုသောအခါ၊ ရလဒ်သည် object ရှိ bytes အရေအတွက်ဖြစ်ပြီး၊ object ကို array တစ်ခု ချထားရန် လိုအပ်သော padding များ အပါအဝင်ဖြစ်ပါသည် - n elements များရှိသော array တစ်ခု၏ အရွယ်အစားသည် element တစ်ခု၏ အရွယ်အစား၏ n ဆဖြစ်ပါသည်။ အော်ပရေတာကို function အမျိုးအစား၊ သို့မဟုတ် မပြည့်စုံသော အမျိုးအစား၊ သို့မဟုတ် bit-field ၏ operand သို့ အသုံးပြု၍မရပါ။ ရလဒ်သည် unsigned integral constant တစ်ခုဖြစ်ပါသည်၊ သီးခြား အမျိုးအစားသည် implementation-defined ဖြစ်ပါသည်။ စံချိန်စံညွှန်း header (နောက်ဆက်တွဲ B ကို ကြည့်ပါ) သည် ဤအမျိုးအစားကို size_t အဖြစ် သတ်မှတ်ပါသည်။

## A.7.5 Casts

အမျိုးအစားတစ်ခု၏ ကွင်းစကွင်းပိတ်ထားသော အမည် ရှေ့တွင်ရှိသော unary expression သည် expression ၏ တန်ဖိုးကို အမည်ရှိသော အမျိုးအစားသို့ ပြောင်းလဲခြင်းကို ဖြစ်စေပါသည်။

cast-expression: unary expression (type-name) cast-expression

ဤတည်ဆောက်ပုံကို cast ဟုခေါ်ပါသည်။ အမည်များကို Par.A.8.8 တွင် ဖော်ပြထားပါသည်။ ပြောင်းလဲမှုများ၏ အကျိုးသက်ရောက်မှုများကို Par.A.6 တွင် ဖော်ပြထားပါသည်။ Cast ပါသော expression သည် lvalue မဟုတ်ပါ။

## A.7.6 Multiplicative Operators

Multiplicative အော်ပရေတာများ *၊ /၊ နှင့် % တို့သည် ဘယ်မှညာ အုပ်စုဖွဲ့ပါသည်။

multiplicative-expression: multiplicative-expression * cast-expression multiplicative-expression / cast-expression multiplicative-expression % cast-expression

- နှင့် / ၏ operands များတွင် arithmetic အမျိုးအစားရှိရမည်၊ % ၏ operands များတွင် integral အမျိုးအစားရှိရမည်။ သာမန် arithmetic conversions များကို operands များပေါ်တွင် လုပ်ဆောင်ပြီး ရလဒ်၏ အမျိုးအစားကို ကြိုတင်ခန့်မှန်းပါသည်။

Binary * အော်ပရေတာသည် မြှောက်ခြင်းကို ညွှန်ပြပါသည်။

Binary / အော်ပရေ

တာသည် ဘေဒကို ထုတ်ပေးပြီး၊ % အော်ပရေတာသည် ပထမ operand ကို ဒုတိယ operand ဖြင့် စားခြင်း၏ အကြွင်းကို ထုတ်ပေးပါသည်၊ အကယ်၍ ဒုတိယ operand သည် 0 ဖြစ်လျှင်၊ ရလဒ်ကို သတ်မှတ်မထားပါ။ မဟုတ်လျှင်၊ (a/b)*b + a%b သည် a နှင့် ညီမျှကြောင်း အမြဲမှန်ပါသည်။ အကယ်၍ operands နှစ်ခုစလုံးသည် အနုတ်လက္ခဏာမဟုတ်လျှင်၊ အကြွင်းသည် အနုတ်လက္ခဏာမဟုတ်ပြီး စားကိန်းထက် သေးငယ်ပါသည်၊ မဟုတ်လျှင်၊ အကြွင်း၏ ပကတိတန်ဖိုးသည် စားကိန်း၏ ပကတိတန်ဖိုးထက် သေးငယ်ကြောင်းသာ အာမခံပါသည်။

## A.7.7 Additive Operators

Additive အော်ပရေတာများ + နှင့် - တို့သည် ဘယ်မှညာ အုပ်စုဖွဲ့ပါသည်။ အကယ်၍ operands များတွင် arithmetic အမျိုးအစားရှိလျှင်၊ သာမန် arithmetic conversions များကို လုပ်ဆောင်ပါသည်။ အော်ပရေတာတစ်ခုစီအတွက် နောက်ထပ် အမျိုးအစားဖြစ်နိုင်ခြေများ အချို့ရှိပါသည်။

additive-expression: multiplicative-expression additive-expression + multiplicative-expression additive-expression - multiplicative-expression

- အော်ပရေတာ၏ ရလဒ်သည် operands များ၏ ပေါင်းလဒ်ဖြစ်ပါသည်။ Array တစ်ခုရှိ object တစ်ခုသို့ pointer နှင့် မည်သည့် integral အမျိုးအစား၏ တန်ဖိုးမဆို ပေါင်းနိုင်ပါသည်။ နောက်ဆုံးကို pointer က ညွှန်ပြနေသော object ၏ အရွယ်အစားဖြင့် မြှောက်၍ address offset သို့ ပြောင်းလဲပါသည်။ ပေါင်းလဒ်သည် မူရင်း pointer နှင့် အမျိုးအစားတူ pointer တစ်ခုဖြစ်ပြီး၊ မူရင်း object မှ သင့်လျော်စွာ offset လုပ်ထားသော array တူရှိ အခြား object တစ်ခုကို ညွှန်ပြပါသည်။ ထို့ကြောင့် အကယ်၍ P သည် array တစ်ခုရှိ object တစ်ခုသို့ pointer တစ်ခုဖြစ်လျှင်၊ expression P+1 သည် array ရှိ နောက် object သို့ pointer တစ်ခုဖြစ်ပါသည်။ အကယ်၍ ပေါင်းလဒ် pointer သည် array ၏ နယ်နိမိတ်ပြင်ပတွင် ညွှန်ပြလျှင်၊ အမြင့်ဆုံးအဆုံး ကျော်လွန်သော ပထမတည်နေရာမှအပ၊ ရလဒ်ကို သတ်မှတ်မထားပါ။

Array ၏ အဆုံးနှင့် ကျော်လွန်ပြီး pointers များအတွက် ပြဋ္ဌာန်းချက်သည် အသစ်ဖြစ်ပါသည်။ ၎င်းသည် array ၏ elements များပေါ်တွင် loop ပတ်ခြင်းအတွက် အဖြစ်များသော idiom ကို တရားဝင်စေပါသည်။

- အော်ပရေတာ၏ ရလဒ်သည် operands များ၏ ခြားနားချက်ဖြစ်ပါသည်။ မည်သည့် integral အမျိုးအစား၏ တန်ဖိုးမဆို pointer မှ နုတ်နိုင်ပြီး၊ ထို့နောက် ပေါင်းခြင်းအတွက် တူညီသော ပြောင်းလဲမှုများနှင့် အခြေအနေများ အသုံးချပါသည်။

အကယ်၍ အမျိုးအစားတူ objects နှစ်ခု၏ pointers နှစ်ခုကို နုတ်လျှင်၊ ရလဒ်သည် ညွှန်ပြထားသော objects များကြား displacement ကို ကိုယ်စားပြုသော signed integral တန်ဖိုးဖြစ်ပါသည်၊ ဆက်တိုက် objects များသို့ pointers များသည် 1 ဖြင့် ကွာခြားပါသည်။ ရလဒ်၏ အမျိုးအစားကို စံချိန်စံညွှန်း header တွင် ptrdiff_t အဖြစ် သတ်မှတ်ထားပါသည်။ Pointers များသည် array တူရှိ objects များကို ညွှန်ပြခြင်း မရှိလျှင် တန်ဖိုးကို သတ်မှတ်မထားပါ၊ သို့သော်၊ အကယ်၍ P သည် array ၏ နောက်ဆုံး member ကို ညွှန်ပြလျှင်၊ (P+1)-P သည် တန်ဖိုး 1 ရှိပါသည်။

[နောက်ဆက်တွဲရှိပါသည်...]