# Third-party material / مواد الجهات الأخرى

Declared pinned Gradle dependencies and their locally cached POM metadata are retained below and in `third_party/metadata/`. License declarations describe those artifacts and do not relicense the application. The Gradle wrapper is retained unchanged. `LICENSES/Apache-2.0.txt` was obtained from https://www.apache.org/licenses/LICENSE-2.0.txt . License files embedded in the delivered APK, when present, are copied unchanged under `LICENSES/apk-embedded/`. This is a packaging inventory, not a newly generated full resolved dependency/SBOM audit.

هذه قائمة الاعتماديات المثبتة في ملفات Gradle وبيانات POM المحلية المحفوظة في `third_party/metadata/`. تصريحات الترخيص تخص تلك الاعتماديات ولا تعيد ترخيص التطبيق. احتُفظ بـGradle wrapper دون تغيير. أُخذ نص Apache من موقعه الرسمي، وحُفظت ملفات الترخيص المضمنة في APK كما هي عند وجودها. هذا جرد للتجهيز وليس تدقيقاً جديداً شاملاً لكل الاعتماديات العابرة.

- `androidx.appcompat:appcompat:1.7.0` — The Apache Software License, Version 2.0
- `androidx.cardview:cardview:1.0.0` — The Apache Software License, Version 2.0
- `androidx.constraintlayout:constraintlayout:2.1.4` — The Apache Software License, Version 2.0
- `androidx.recyclerview:recyclerview:1.3.2` — The Apache Software License, Version 2.0
- `androidx.test.espresso:espresso-core:3.6.1` — The Apache Software License, Version 2.0
- `androidx.test.ext:junit:1.2.1` — The Apache Software License, Version 2.0
- `com.android.tools.build:gradle:8.13.0` — The Apache Software License, Version 2.0
- `com.android.tools:desugar_jdk_libs:2.1.5` — GNU General Public License, version 2, with the Classpath Exception
- `com.google.android.material:material:1.12.0` — The Apache Software License, Version 2.0
- `com.wireguard.android:tunnel:1.0.20250531` — The Apache Software License, Version 2.0
- `io.github.tim06:vpnprotocols-openvpn:3.0.4` — The Apache License, Version 2.0
- `junit:junit:4.13.2` — Eclipse Public License 1.0
- `org.json:json:20240303` — Public Domain

## Native runtime audit / تدقيق المكتبات الأصلية

The complete local snapshot retains `app/libs/outline-tun2socks.jar` and `app/src/main/jniLibs/arm64-v8a/libgojni.so` because removing them breaks the source build. The native Go build metadata identifies `github.com/Jigsaw-Code/outline-go-tun2socks` with a zero pseudo-version and a local replacement, not an exact source revision. Its known dependencies include outline-ss-server v1.4.0, eycorsican/go-tun2socks v1.16.11, go-shadowsocks2 at 75d43273f5a5, x/crypto v0.1.0, x/mobile at43a038452099 and x/sys v0.1.0. The official Outline upstream now resolves to https://github.com/OutlineFoundation/outline-go-tun2socks ; the Apache license fetched from that upstream is retained, but it does not establish an exact native-source match or complete transitive notices.

`io.github.tim06:vpnprotocols-openvpn:3.0.4` is declared Apache-2.0 by its Maven POM (retained in `third_party/metadata`). Its upstream URL https://github.com/tim06/VPNProtocols returned404 during preparation. The official Maven Central Java/SWIG sources JAR is included in `third_party/sources`; it does not contain the corresponding OpenVPN C++ native source. An older local report describes AGPL/OpenVPN obligations while the POM describes the wrapper as Apache; the wrapper POM alone does not resolve the native license. Matching source, revision/build instructions and required native/transitive licenses/notices remain unestablished. Do not label the APK fully license-cleared.

Official artifact/source reference: https://repo.maven.apache.org/maven2/io/github/tim06/vpnprotocols-openvpn/3.0.4/ . WireGuard tunnel 1.0.20250531 identifies https://git.zx2c4.com/wireguard-android as its source repository in the retained POM.

احتُفظ بملفي Outline اللازمين للبناء لأن حذفهما يعطل اكتمال المصدر. تشير بيانات Go المضمنة إلى مشروع Outline عبر مسار محلي وإصدار صفري دون تحديد commit مطابق. أُرفقت رخصة Apache من المصدر الرسمي الحالي، لكنها لا تثبت تطابق النسخة الأصلية أو اكتمال إشعارات اعتمادياتها.

يعلن POM لمكتبة OpenVPN الوسيطة 3.0.4 ترخيص Apache-2.0، لكن رابط مستودعها أعاد404. أُرفق ملف المصادر الرسمي من Maven Central وهو Java/SWIG فقط دون مصدر C++ الأصلي المقابل. يوجد تعارض غير محسوم بين وصف تقرير محلي قديم لالتزامات AGPL/OpenVPN ووصف POM للغلاف الوسيط. يلزم تحديد مصدر ومراجعة وتعليمات بناء وتراخيص وإشعارات المكتبات الأصلية والاعتماديات قبل النشر العام. حُفظت الملفات اللازمة للبناء والمعلومات المعروفة دون الادعاء بأن تدقيق الترخيص اكتمل. رخصة Apache لا تشترط وحدها إرفاق المصدر الكامل لتوزيع الملف الثنائي.

## Existing public-provider material / مواد مزوّد عامة موجودة

`VpnBookFetcher.java` contains built-in shared VPNBook client certificate/key and default provider credentials, identified by the existing source as provider material for offline fallback. They were retained as application source, not introduced by this packaging. Current official endpoints could not be retrieved during the check, so current validity/byte equivalence is not established. Parser and log-sanitizer tests also contain PEM markers/synthetic snippets. These are distinct from excluded developer signing keys and user VPN profiles.

يتضمن مصدر VPNBook إعدادات اعتماد ومفتاح عميل مشتركاً يصفهما الكود القائم بمواد المزود العامة للاستخدام الاحتياطي؛ احتُفظ بهما كما هما ولم يُضافا أثناء التجهيز. تعذر جلب العناوين الرسمية الحالية، لذا لم يثبت تطابقها أو صلاحيتها الآن. وتوجد علامات PEM وعينات اصطناعية في اختبارات التحليل وتنقيح السجل؛ وهي منفصلة عن مفاتيح توقيع المطور وإعدادات VPN الشخصية المستبعدة.
