# نحوه نصب

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### نصب

```bash
agy plugin install https://github.com/crooy/i-have-adhd
```

### بررسی صحت نصب

```bash
agy plugin list
```

### به‌روزرسانی

```bash
agy plugin uninstall mand
agy plugin install https://github.com/crooy/i-have-adhd
```

### حذف نصب

```bash
agy plugin uninstall mand
```

یا اگر می‌خواهید نصب بماند اما غیرفعال شود: `agy plugin disable mand`.

### همیشه فعال (اختیاری)

این خطوط را به فایل `~/.gemini/GEMINI.md` اضافه کنید:

```markdown
## Output style

پاسخ کوتاه و کنش‌محور بده. هر پاسخ را طوری شکل بده که بتوان بلافاصله بر اساس آن عمل کرد:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. پاسخ به انگلیسی، صرف‌نظر از زبان ورودی یا کد.
11. هرگاه نمودار بتواند معنا را منتقل کند، نمودار را بر متن یا کد ترجیح بده.
12. No preamble, no recaps, no closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>AstronClaw (مهارت سفارشی)</strong></summary>

AstronClaw از وارد کردن فایل Markdown به عنوان یک مهارت سفارشی پشتیبانی می‌کند. این روش از فایل `SKILL.md` موجود استفاده می‌کند. برای جزئیات بارگذاری و مدیریت، به [راهنمای رسمی مهارت‌ها](https://github.com/iflytek/astronclaw-tutorial/blob/main/docs/guide/astronclaw/skills.md) مراجعه کنید.

این مراحل بر اساس مستندات AstronClaw نوشته شده، اما با این مهارت خاص آزمایش نشده است. لطفاً قبل از فعال‌سازی، دستورالعمل‌های واردشده را بررسی کنید.

### نصب

1. فایل [SKILL.md اصلی](https://raw.githubusercontent.com/crooy/i-have-adhd/main/skills/mand/SKILL.md) را دانلود کرده و با نام `SKILL.md` ذخیره کنید. قبل از بارگذاری، محتوای آن را مرور کنید.
2. در AstronClaw، بخش **我的技能 (My skills)** را باز کنید، **新建 (New)** را انتخاب کرده و آن فایل `.md` را بارگذاری کنید.
3. مطمئن شوید نام مهارت واردشده `mand` است. برای کنترل در دسترس بودن آن، از گزینه **启用/禁用 (Enable/Disable)** استفاده کنید.

فقط فایل Markdown مهارت مورد نیاز است. با بارگذاری این فایل، فایل به AstronClaw ارسال می‌شود؛ مانیفست‌های پلاگین و هوک‌های موجود در ریپازیتوری بخشی از این تنظیمات نیستند.

### بررسی و فعال‌سازی

تأیید کنید که `mand` در **My skills** ظاهر شده است. از گزینه **下载 (Download)** برای مقایسه دستورالعمل‌های واردشده با نسخه اصلی استفاده کنید، سپس آن را فعال کرده و دستور زیر را امتحان کنید:

```text
Use the mand skill for this conversation. Explain how to create an empty Git repository in a new folder.
```

بررسی کنید که پاسخ با اقدام عملی شروع شود و مراحل شماره‌گذاری شده باشند. این یک بررسی دستی از مهارت واردشده است و موفقیت‌آمیز بودن بارگذاری به تنهایی تأیید نمی‌کند که قوانین پاسخ‌دهی اعمال می‌شوند.

### نکته فعال‌سازی

AstronClaw هم از درخواست‌های صریح و هم از فراخوانی خودکار مهارت پشتیبانی می‌کند. راهنمای آن مشخص نمی‌کند که آیا `disable-model-invocation: true` را رعایت می‌کند یا خیر، بنابراین زمانی که نمی‌خواهید مهارت در دسترس باشد، از گزینه **Disable** استفاده کنید. نیازی به استفاده از دستور اسلش `/mand` نیست.

این مهارت به دستیار دستور می‌دهد تا زمانی که نگویید `stop mand` یا `normal mode`، این سبک را برای مکالمه حفظ کند. این دستور، تنظیمات پلتفرم را تغییر نمی‌دهد؛ برای شروع یک نشست تازه بدون این مهارت، آن را غیرفعال کرده و یک مکالمه جدید شروع کنید.

### به‌روزرسانی

آخرین نسخه `SKILL.md` اصلی را دانلود کنید. اگر نسخه واردشده را سفارشی کرده‌اید، ابتدا با استفاده از **下载 (Download)** از آن نسخه پشتیبان بگیرید. برای جایگزینی کامل، ورودی قدیمی `mand` را حذف کنید، مراحل واردسازی را تکرار کرده و دستور بررسی را در یک مکالمه جدید اجرا کنید.

### حذف نصب

در بخش **My skills**، گزینه `mand` را انتخاب و **删除 (Delete)** را بزنید، سپس یک مکالمه جدید شروع کنید. اگر می‌خواهید نسخه واردشده را برای بعداً نگه دارید، به جای حذف، آن را **Disable** کنید.

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### نصب

```bash
claude plugin marketplace add crooy/i-have-adhd
claude plugin install mand@mand
```

سپس دستور `/mand` را تایپ کنید.

### بررسی صحت نصب

```bash
claude plugin list
```

### به‌روزرسانی

```bash
claude plugin marketplace update mand
claude plugin update mand@mand
```

### حذف نصب

```bash
claude plugin uninstall mand
claude plugin marketplace remove mand
```

یا اگر می‌خواهید نصب بماند اما غیرفعال شود: `claude plugin disable mand`.

### همیشه فعال (اختیاری)

یک هوک `SessionStart` مجموعه قوانین کامل را در ابتدای هر نشست بارگذاری می‌کند و نیازی به تایپ `/mand` نیست:

```bash
touch ~/.claude/.mand-always
```

اگر از دایرکتوری پیکربندی سفارشی Claude استفاده می‌کنید، پرچم را در آنجا ایجاد کنید:

```bash
touch "$CLAUDE_CONFIG_DIR/.mand-always"
```

بازگشت به حالت فعال‌سازی دستی:

```bash
rm ~/.claude/.mand-always
```

این هوک تنها زمانی اجرا می‌شود که فایل پرچم وجود داشته باشد، بنابراین نصب پلاگین به خودی خود چیزی را تغییر نمی‌دهد. دستور "stop mand" همچنان آن را برای نشست جاری خاموش می‌کند.

</details>

<details>
<summary><strong>Codex</strong></summary>

### نصب

```bash
codex plugin marketplace add crooy/i-have-adhd --ref main
codex plugin add mand@mand
```

برای فراخوانی صریح مهارت، دستور `$mand` را تایپ کنید. Codex آن را به صورت خودکار فعال نمی‌کند.

### بررسی صحت نصب

```bash
codex plugin list
```

### به‌روزرسانی

```bash
codex plugin marketplace upgrade mand
codex plugin remove mand
codex plugin add mand@mand
```

### حذف نصب

```bash
codex plugin remove mand
codex plugin marketplace remove mand
```

### همیشه فعال (اختیاری)

این خطوط را به فایل `~/.codex/AGENTS.md` اضافه کنید:

```markdown
## Output style

پاسخ کوتاه و کنش‌محور بده. هر پاسخ را طوری شکل بده که بتوان بلافاصله بر اساس آن عمل کرد:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. پاسخ به انگلیسی، صرف‌نظر از زبان ورودی یا کد.
11. هرگاه نمودار بتواند معنا را منتقل کند، نمودار را بر متن یا کد ترجیح بده.
12. No preamble, no recaps, no closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI بازارچه (marketplace) پلاگین ندارد، بنابراین دو روش بومی وجود دارد: یک **دستور سفارشی** (اختیاری، تا زمانی که فراخوانی نکنید خاموش است) یا یک **افزونه** (پس از نصب همیشه فعال است). روش دستور با حالت پیش‌فرض این مهارت همخوانی دارد؛ مگر اینکه بخواهید قوانین در هر نشست اعمال شوند، این روش را انتخاب کنید.

### نصب (دستور، فعال‌سازی دستی)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/crooy/i-have-adhd/main/skills/mand/agents/gemini.toml \
  -o ~/.gemini/commands/mand.toml
```

یک نشست جدید شروع کنید و `/mand` را تایپ کنید. این حالت برای آن نشست فعال می‌ماند.

### نصب (افزونه، همیشه فعال)

```bash
gemini extensions install https://github.com/crooy/i-have-adhd
```

این افزونه `GEMINI.md` را بارگذاری می‌کند که مهارت کامل را وارد می‌کند، بنابراین قوانین از همان پیام اول اعمال می‌شوند. `git` باید نصب باشد.

### بررسی صحت نصب

```bash
gemini extensions list          # روش افزونه
ls ~/.gemini/commands           # روش دستور: فایل mand.toml باید موجود باشد
```

یا در یک نشست `/` را تایپ کنید و تأیید کنید که `mand` در لیست است.

### به‌روزرسانی

```bash
gemini extensions update mand    # روش افزونه
# روش دستور: دستور curl بالا را مجدداً اجرا کنید
```

### حذف نصب

```bash
gemini extensions uninstall mand    # روش افزونه
rm ~/.gemini/commands/mand.toml     # روش دستور
```

</details>

<details>
<summary><strong>GitHub Copilot (در VS Code و Copilot CLI)</strong></summary>

Copilot مهارت‌های عامل (Agent Skills) را به صورت بومی می‌خواند: همان فایل `SKILL.md` بدون نیاز به تبدیل. این ابزار پوشه‌های `.github/skills/`، `.claude/skills/` و `.agents/skills/` در پروژه، و همچنین `~/.copilot/skills/`، `~/.claude/skills/` و `~/.agents/skills/` را به صورت سراسری اسکن می‌کند.

### نصب

```bash
npx skills add crooy/i-have-adhd -a github-copilot        # فقط این پروژه
npx skills add crooy/i-have-adhd -a github-copilot -g     # همه پروژه‌ها
```

بدون استفاده از CLI، پوشه مهارت را در هر دایرکتوری که Copilot اسکن می‌کند کپی کنید:

```bash
git clone https://github.com/crooy/i-have-adhd
mkdir -p ~/.copilot/skills
cp -R mand/skills/mand ~/.copilot/skills/
```

### بررسی صحت نصب

در ورودی چت `/` را تایپ کنید و تأیید کنید که `mand` ظاهر می‌شود. یا:

```bash
npx skills list
npx skills ls -g    # اگر به صورت سراسری نصب شده است
```

### به‌روزرسانی

```bash
npx skills update mand
```

یا پس از `git pull`، پوشه را مجدداً کپی کنید.

### حذف نصب

```bash
npx skills remove mand
```

یا پوشه `mand` را از دایرکتوری مهارت‌هایی که در آن نصب شده حذف کنید.

### نکته فعال‌سازی

Copilot گزینه `disable-model-invocation` را رعایت می‌کند: تا زمانی که مهارت را فراخوانی نکنید، هیچ قانونی اعمال نمی‌شود (مشابه Claude Code، همان‌طور که در [#60](https://github.com/ayghri/i-have-adhd/pull/60) آزمایش شده است).

### همیشه فعال (اختیاری)

بلوک زیر را به فایل `.github/copilot-instructions.md` در پروژه اضافه کنید (Copilot آن را در هر چت می‌خواند):

```markdown
## Output style

پاسخ کوتاه و کنش‌محور بده. هر پاسخ را طوری شکل بده که بتوان بلافاصله بر اساس آن عمل کرد:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. پاسخ به انگلیسی، صرف‌نظر از زبان ورودی یا کد.
11. هرگاه نمودار بتواند معنا را منتقل کند، نمودار را بر متن یا کد ترجیح بده.
12. No preamble, no recaps, no closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Hermes</strong></summary>

### نصب

```bash
hermes skills install crooy/i-have-adhd/skills/mand
```

دستور `/mand` را تایپ کنید. این مهارت در `~/.hermes/skills/` نصب شده و به عنوان یک دستور اسلش در شروع نشست بعدی در دسترس قرار می‌گیرد.

اگر ترجیح می‌دهید ابتدا مرور کنید؟ این ریپازیتوری را به عنوان منبع مهارت (یک "tap") اضافه کنید، سپس جستجو و نصب کنید:

```bash
hermes skills tap add crooy/i-have-adhd
hermes skills search mand
hermes skills install crooy/i-have-adhd/skills/mand
```

### بررسی صحت نصب

```bash
hermes skills list
```

### به‌روزرسانی

```bash
hermes skills update mand
```

### حذف نصب

```bash
hermes skills uninstall mand
```

یا برای حذف کامل منبع نیز: `hermes skills tap remove crooy/i-have-adhd`.

### همیشه فعال (اختیاری)

این خطوط را به فایل `AGENTS.md` در دایرکتوری کاری خود (Hermes آن را برای هر دایرکتوری کاری بارگذاری می‌کند) یا به فایل شخصیت `SOUL.md` برای هر نشست اضافه کنید:

```markdown
## Output style

پاسخ کوتاه و کنش‌محور بده. هر پاسخ را طوری شکل بده که بتوان بلافاصله بر اساس آن عمل کرد:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. پاسخ به انگلیسی، صرف‌نظر از زبان ورودی یا کد.
11. هرگاه نمودار بتواند معنا را منتقل کند، نمودار را بر متن یا کد ترجیح بده.
12. No preamble, no recaps, no closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### نصب

یک نشست Kimi Code شروع کنید، سپس:

1. دستور `/plugins` را اجرا کنید.
2. گزینه **Custom** را انتخاب کنید.
3. آدرس `https://github.com/crooy/i-have-adhd` را پیست کرده و `Enter` را بزنید.
4. گزینه **Trust and install** را انتخاب کنید.

برای فراخوانی صریح مهارت، از دستور اسلش `/skill:mand` استفاده کنید.

### به‌روزرسانی

در نشست Kimi Code، دستور `/plugins` را بزنید، نشانگر را روی **mand** ببرید و کلید `R` را فشار دهید.

### حذف نصب

در نشست Kimi Code، دستور `/plugins` را بزنید، نشانگر را روی **mand** ببرید و کلید `D` را فشار دهید.

</details>

<details>
<summary><strong>OpenCode</strong></summary>

پلاگین از OpenCode V1 **نسخه 1.18.29 و جدیدتر** و V2 پشتیبانی می‌کند. مهارت و دستور `/mand` را ثبت می‌کند و حالت همیشه فعال را به‌صورت اختیاری ارائه می‌دهد. نسخه‌های قدیمی‌تر V1 باید ارتقا یابند یا از پلاگین نسخه قبلی مهارت استفاده کنند.

### نصب

برای استفاده در همه پروژه‌ها:

```bash
git clone https://github.com/crooy/i-have-adhd ~/.config/opencode/vendor/mand
mkdir -p ~/.config/opencode/plugins
cat > ~/.config/opencode/plugins/mand.js <<'EOF'
export { default } from '../vendor/mand/.opencode/plugins/mand.mjs';
EOF
```

برای نصب فعلی V1، ورودی `plugin` را در `opencode.json` نگه دارید. اگر به فایل بارگذار بالا تغییر می‌دهید، آن ورودی را حذف کنید.

یک نشست جدید شروع کنید و `/mand` را وارد کنید. قوانین تا زمانی که `stop mand` یا `normal mode` را بگویید فعال می‌مانند.

#### فقط مهارت و دستور (بدون حالت همیشه فعال)

روش دیگر این است که مهارت و دستور را از ریپازیتوری به پوشه‌های سراسری OpenCode کپی کنید:

```bash
mkdir -p ~/.config/opencode/skills/mand ~/.config/opencode/commands
cp skills/mand/SKILL.md ~/.config/opencode/skills/mand/SKILL.md
cp .opencode/command/mand.md ~/.config/opencode/commands/mand.md
```

### بررسی صحت نصب

OpenCode را اجرا کنید، `/` را وارد کنید و مطمئن شوید `mand` در فهرست دستورات دیده می‌شود.

### به‌روزرسانی

```bash
git -C ~/.config/opencode/vendor/mand pull
```

در روش نصب با کپی، ریپازیتوری را به‌روزرسانی کرده و هر دو فایل را دوباره کپی کنید.

### حذف نصب

فایل `~/.config/opencode/plugins/mand.js` را حذف کنید. در روش نصب با کپی، `~/.config/opencode/skills/mand/` و `~/.config/opencode/commands/mand.md` را حذف کنید. برای نصب فعلی V1 با تنظیمات، ورودی `plugin` مربوط را حذف کنید.

### همیشه فعال (اختیاری)

به پلاگین نیاز دارد. ساختن فایل پرچم، تمام قوانین را در هر نوبت به پرامپت سیستم اضافه می‌کند:

```bash
touch ~/.config/opencode/.mand-always
```

دستور `stop mand` یا `normal mode` از عامل می‌خواهد در نشست جاری به سبک پاسخ معمول برگردد. برای توقف تزریق خودکار، فایل پرچم را حذف کنید:

```bash
rm ~/.config/opencode/.mand-always
```

اگر `XDG_CONFIG_HOME` تنظیم شده است، در این مسیرها `~/.config` را با آن پوشه جایگزین کنید.

</details>

<details>
<summary><strong>Pi</strong></summary>

Pi این ریپازیتوری را به عنوان یک بسته بومی کشف می‌کند: پوشه `extensions/` حالت پایدار نشست را فراهم می‌کند و `skills/` نقطه ورود Agent Skills را در دسترس نگه می‌دارد.

### نصب

```bash
pi install https://github.com/crooy/i-have-adhd
```

یک نشست جدید Pi شروع کنید. خروجی کوتاه و کنش‌محور را برای نشست جاری تغییر دهید:

```text
/mand
```

پاورقی (footer) تا زمانی که این حالت فعال است، `● MAND ON` را نشان می‌دهد. برای خاموش کردن، مجدداً همین دستور را اجرا کنید یا صریحاً بنویسید:

```text
/mand on
/mand off
stop mand
```

مانند هوک Claude Code، این افزونه مجموعه قوانین را یک‌بار به مکالمه اضافه می‌کند (به جای بازنویسی پرامپت سیستم در هر درخواست) و پس از فشرده‌سازی (compaction) که آن را حذف می‌کند، مجدداً اضافه می‌کند.

دستور Agent Skills موجود نیز به عنوان یک نام مستعار در دسترس است:

```text
/skill:mand
```

شروع یک نشست جدید Pi با این حالت به صورت پیش‌فرض فعال:

```bash
pi --mand
```

### بررسی صحت نصب

```bash
pi list
```

تأیید کنید که بسته GitHub در لیست است، سپس `/mand` را تایپ کرده و بررسی کنید که `● MAND ON` در پاورقی ظاهر شود.

### به‌روزرسانی

```bash
pi update https://github.com/crooy/i-have-adhd
```

یا همه بسته‌های Pi که پین نشده‌اند را با `pi update --extensions` به‌روزرسانی کنید.

### حذف نصب

```bash
pi remove https://github.com/crooy/i-have-adhd
```

### همیشه فعال (اختیاری)

یک پرچم در دایرکتوری پیکربندی عامل Pi ایجاد کنید:

```bash
touch ~/.pi/agent/.mand-always
```

این افزونه پرچم را در هر نشست جدید، از سر گرفته شده، شاخه‌دار شده یا بارگذاری مجدد بررسی می‌کند. یک انتخاب ذخیره‌شده برای نشست جاری بر این پیش‌فرض ارجحیت دارد، بنابراین `stop mand` آن نشست را غیرفعال نگه می‌دارد.

بازگشت به حالت فعال‌سازی دستی:

```bash
rm ~/.pi/agent/.mand-always
```

### فایل پیکربندی (اختیاری)

فایل `~/.pi/agent/mand.json` را در دایرکتوری پیکربندی عامل Pi ایجاد کنید:

```json
{
  "alwaysOn": true,
  "hideStatus": true
}
```

- `alwaysOn`: هر نشست را با قوانین فعال شروع می‌کند — مشابه فایل پرچم `.mand-always` که همچنان کار می‌کند.
- `hideStatus`: ورودی نوار وضعیت `● MAND ON` را مخفی نگه می‌دارد؛ قوانین و دستور `/mand` همچنان کار می‌کنند.

این فایل یک‌بار در شروع افزونه خوانده می‌شود، بنابراین پس از تغییر آن، Pi را مجدداً راه‌اندازی کنید. یک انتخاب ذخیره‌شده برای نشست جاری بر `alwaysOn` ارجحیت دارد، بنابراین `stop mand` آن نشست را غیرفعال نگه می‌دارد.

اگر متغیر `PI_CODING_AGENT_DIR` تنظیم شده باشد، فایل `.mand-always` را در آن دایرکتوری قرار دهید. پس از تغییر پرچم، دستور `/reload` را اجرا کنید یا یک نشست جدید شروع کنید.

</details>

<details>
<summary><strong>Oh My Pi (OMP)</strong></summary>

### نصب

```bash
omp plugin marketplace add crooy/i-have-adhd
omp plugin install --scope user mand@mand
```

یک نشست جدید OMP شروع کنید و برای تغییر حالت، دستور `/mand` را اجرا کنید.

### به‌روزرسانی

```bash
omp plugin marketplace update mand
omp plugin upgrade --scope user mand@mand
```

### حذف نصب

```bash
omp plugin uninstall --scope user mand@mand
omp plugin marketplace remove mand
```

</details>

<details>
<summary><strong>Qwen Code</strong></summary>

### نصب

```bash
qwen extensions install crooy/i-have-adhd
```

Qwen Code از مخفف GitHub پشتیبانی می‌کند و ریپازیتوری را به عنوان یک افزونه بومی نصب می‌کند. این افزونه مهارت را در پوشه `skills/` کشف می‌کند.

برای فراخوانی صریح مهارت، دستور `/mand` را تایپ کنید. نصب افزونه تا زمانی که مهارت فراخوانی نشود، خروجی را تغییر نمی‌دهد.

### بررسی صحت نصب

```bash
qwen extensions list
```

سپس یک نشست جدید Qwen Code شروع کرده و اجرا کنید:

```text
/skills
```

تأیید کنید که `mand` در لیست ظاهر می‌شود.

### به‌روزرسانی

```bash
qwen extensions update mand
```

### حذف نصب

```bash
qwen extensions uninstall mand
```

</details>

<details>
<summary><strong>Zed</strong></summary>

عامل (Agent) در Zed مهارت‌های عامل را به صورت بومی و با همان فرمت `SKILL.md` بدون نیاز به تبدیل می‌خواند. توجه داشته باشید که "Rules" قدیمی Zed در کنار دستورالعمل‌های `AGENTS.md` با Skills جایگزین شده‌اند.

### نصب

در پنل Agent، مدیر مهارت‌ها (Skills manager) را باز کرده و **Create skill from URL** (همچنین در پالت دستورات به عنوان `agent: create skill from url`) را انتخاب کنید، سپس آدرس زیر را پیست کنید:

```text
https://github.com/crooy/i-have-adhd/blob/main/skills/mand/SKILL.md
```

آن را در محدوده **User** برای همه پروژه‌ها، یا در محدوده **Project** برای یک پروژه ذخیره کنید. سپس در پنل Agent دستور `/mand` را تایپ کنید.

اگر فایل‌سیستم را ترجیح می‌دهید؟ ریپازیتوری را کلون کرده و پوشه مهارت را در دایرکتوری مهارت‌های کاربر خود رها کنید:

```bash
git clone https://github.com/crooy/i-have-adhd
mkdir -p ~/.agents/skills
cp -R mand/skills/mand ~/.agents/skills/
```

### بررسی صحت نصب

مدیر مهارت‌ها را در پنل Agent باز کنید و تأیید کنید که `mand` در لیست است. یا `/` را تایپ کنید و تأیید کنید که ظاهر می‌شود.

### به‌روزرسانی

مجدداً از همان URL وارد کنید (بازنویسی می‌شود)، یا پس از `git pull` پوشه را مجدداً کپی کنید.

### حذف نصب

`mand` را از مدیر مهارت‌ها حذف کنید، یا `~/.agents/skills/mand` را پاک کنید.

### همیشه فعال (اختیاری)

این خطوط را به فایل شخصی `~/.config/zed/AGENTS.md` خود اضافه کنید:

```markdown
## Output style

پاسخ کوتاه و کنش‌محور بده. هر پاسخ را طوری شکل بده که بتوان بلافاصله بر اساس آن عمل کرد:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. پاسخ به انگلیسی، صرف‌نظر از زبان ورودی یا کد.
11. هرگاه نمودار بتواند معنا را منتقل کند، نمودار را بر متن یا کد ترجیح بده.
12. No preamble, no recaps, no closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Cursor، Amp و هر ابزار مهارت‌محور دیگر</strong></summary>

با هر ابزاری که مهارت‌های عامل را می‌خواند کار می‌کند. `-a <agent>` را با ابزار خود جایگزین کنید.

### نصب

```bash
npx skills add crooy/i-have-adhd                  # فقط این فضای کاری
npx skills add crooy/i-have-adhd -g               # همه پروژه‌ها
npx skills add crooy/i-have-adhd -a cursor -y     # فقط یک عامل خاص
npx skills add crooy/i-have-adhd -a opencode -y
```

در چت جدید عامل، دستور `/mand` را تایپ کنید.

بدون استفاده از CLI، پوشه مهارت را در هر مسیری که عامل شما اسکن می‌کند کپی کنید:

```bash
git clone https://github.com/crooy/i-have-adhd
mkdir -p ~/.cursor/skills     # برای Cursor. برای OpenCode از .agents/skills یا مسیر خاص عامل خود استفاده کنید
cp -R mand/skills/mand ~/.cursor/skills/
```

### بررسی صحت نصب

```bash
npx skills list
npx skills ls -g    # اگر به صورت سراسری نصب شده است
```

### به‌روزرسانی

```bash
npx skills update mand
npx skills update -g    # اگر به صورت سراسری نصب شده است
```

### حذف نصب

```bash
npx skills remove mand
npx skills remove mand -g    # اگر به صورت سراسری نصب شده است
```

### همیشه فعال (اختیاری)

این متن را در فایل قوانین پایدار عامل خود پیست کنید. برای Cursor: **Settings → Rules → User Rules**، یا یک قانون پروژه در `.cursor/rules/` با `alwaysApply: true`. برای OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Output style

پاسخ کوتاه و کنش‌محور بده. هر پاسخ را طوری شکل بده که بتوان بلافاصله بر اساس آن عمل کرد:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. پاسخ به انگلیسی، صرف‌نظر از زبان ورودی یا کد.
11. هرگاه نمودار بتواند معنا را منتقل کند، نمودار را بر متن یا کد ترجیح بده.
12. No preamble, no recaps, no closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```
</details>

## نحوه فعال‌سازی

1. **نصب‌شده، اما فراخوانی‌نشده.** در Claude Code، Qwen Code و Codex، تا زمانی که مهارت را صریحاً فراخوانی نکنید، هیچ اتفاقی نمی‌افتد. Claude Code و Qwen Code گزینه `disable-model-invocation: true` را در `SKILL.md` رعایت می‌کنند؛ Codex نیز `policy.allow_implicit_invocation: false` را در `agents/openai.yaml` رعایت می‌کند. سایر ابزارها ممکن است توضیحات هر مهارت را در شروع بارگذاری کرده و خودشان آن را فعال کنند.
2. **شما آن را صریحاً فراخوانی می‌کنید.** در Claude Code یا Qwen Code دستور `/mand`، یا در Codex دستور `$mand` را تایپ کنید. قوانین برای آن نشست فعال می‌مانند. با "stop mand" یا "normal mode" خاموش می‌شوند.
3. **شما فایل `~/.claude/.mand-always` را لمس می‌کنید** (در Claude Code). یک هوک `SessionStart` مجموعه قوانین کامل را از پیام اول، در هر نشست بارگذاری می‌کند.
4. **شما قطعه کد همیشه فعال بالا را اضافه می‌کنید** (در سایر ابزارها). قوانین اصلی را در زمینه پایدار عامل شما نگه می‌دارد.

در Claude Code، Qwen Code و Codex، حد وسطی وجود ندارد: اگر آن را روشن نکرده‌اید، خاموش است.

## عیب‌یابی

**دستور `/mand` در تکمیل خودکار نیست.** عامل را مجدداً راه‌اندازی کنید. فهرست پلاگین‌ها در شروع خوانده می‌شود.

**پرچم همیشه فعال اثری ندارد.** پلاگین را به‌روزرسانی کنید (`claude plugin marketplace update mand` و سپس `claude plugin update mand@mand`) و مجدداً راه‌اندازی کنید. هوک‌ها در شروع خوانده می‌شوند و پرچم به نسخه‌ای از پلاگین نیاز دارد که `hooks/hooks.json` را ارائه می‌دهد.

**دستور `claude plugin marketplace add` با خطا مواجه می‌شود.** از فرم `owner/repo` استفاده کنید. یک مسیر محلی باید به ریشه ریپازیتوری اشاره کند، نه به `.claude-plugin/`.

**نصب شده اما پاسخ‌ها همچنان مقدمه‌چینی می‌کنند.** یک نشست جدید باز کنید. اگر همچنان انحراف وجود داشت، عبارت‌بندی را در `skills/mand/SKILL.md` سخت‌گیرانه‌تر کنید.

**قوانین متفاوتی می‌خواهید.** فورک کنید، `skills/mand/SKILL.md` را ویرایش کنید، سپس نسخه خود را جایگزین کنید:

```bash
claude plugin uninstall mand            # ابتدا نسخه اصلی را حذف کنید:
claude plugin marketplace remove mand   # نام فورک و نسخه اصلی هر دو یکسان است
claude plugin marketplace add <your-username>/mand
claude plugin install mand@mand
```

مجدداً راه‌اندازی کنید، سپس `/mand` را مجدداً فراخوانی کنید.

**مهارت پس از `npx skills add` ناپدید است.** یک چت جدید با عامل شروع کنید. مهارت‌ها در شروع نشست فهرست‌بندی می‌شوند. تأیید کنید که پوشه در جایی که عامل اسکن می‌کند قرار گرفته است (`~/.cursor/skills/` برای Cursor، `.agents/skills/` برای OpenCode) و اینکه `name` در frontmatter با نام پوشه مطابقت دارد.
