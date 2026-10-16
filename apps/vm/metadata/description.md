# VM (QEMU)
ماكينة افتراضية جوه Docker (باستخدام [qemux/qemu](https://github.com/dockur/qemu)) تقدر تثبت فيها **أي نظام تشغيل** وتديره من المتصفح أو من RDP.

## المتطلبات
- المضيف لازم يكون عليه **KVM** (وجود `/dev/kvm`). التطبيق بيمرر الجهاز ده للحاوية، فلو مش موجود الحاوية مش هتشتغل أصلاً.
- لو KVM مش موجود: فعّل Intel VT-x / AMD-V من الـ BIOS، ولو المضيف نفسه جهاز وهمي فعّل عليه Nested Virtualization.

## طريقة الاستخدام
- **ويب كونسول:** من زرار Open (بورت 8006) تتابع تثبيت النظام وتتحكم فيه من المتصفح.
- **نظام التشغيل (BOOT):** اسم توزيعة جاهزة (مثل `ubuntu`, `mint`, `debian`, `fedora`, `arch`, `alpine`, `kali`, `suse`) أو **رابط مباشر** لملف ISO/IMG/QCOW2.
- **ويندوز:** استخدم [dockur/windows](https://github.com/dockur/windows) بدل التطبيق ده، لأنه بيحتوي على الدرايفرز المطلوبة للتثبيت.

## RDP
RDP بيشتغل من جوه نظام التشغيل الضيف، والتطبيق بس بيفتح البورت له.
1. ثبّت النظام من الويب كونسول.
2. فعّل RDP جوه الضيف. لينكس: `sudo apt install xrdp` ثم `sudo systemctl enable --now xrdp`. ويندوز: Settings ← System ← Remote Desktop (نسخة Pro أو أعلى).
3. اتصل على `IP-السيرفر:<RDP Port>` (البورت اللي اخترته في الفورم، والافتراضي 3389).
   - من Arch: `xfreerdp /v:IP-السيرفر:3389 /u:USER /dynamic-resolution +clipboard`
   - من Android: تطبيق Windows App (RD Client)

## حفظ البيانات
القرص الافتراضي بيتحفظ في مجلد `data/storage` الخاص بالتطبيق جوه `app-data` بتاع runtipi. يفضل تعمل Backup قبل أي تعديل كبير.
