# カラムリファレンス

|フィールド名|タイプ|説明|
|:----|:----|:----|
|timestamp|TIMESTAMP|アクション（レコード）のUTCライムスタンプ|
|sdk_version|STRING|データを送信したSDKのバージョン情報|
|endpoint_version|STRING|データを受信したエンドポイントのバージョン情報|
|action|STRING|アクションの名前。基本的に動詞|
|category|STRING|アクションの対象物。基本的に名詞|
|cookie|BOOLEAN|Cookieの利用可否（JS SDKのみ）|
|consent|STRING|データ利用に関する同意情報（JSON文字列）|
|request_id|STRING|SHA256ハッシュで生成されたレコードのユニークID|
|ingestly_id|STRING|デバイス（ブラウザ）を識別するためのユニークID|
|session_id|STRING|セッションID（セッションCookieによって管理される）|
|is_id_new|BOOLEAN|Ingestly IDが新規発行されたものの場合 `true` となる（同一Root IDで最初の数件がtrueとなる場合がある）|
|is_session_new|BOOLEAN|セッションの最初のビーコンの場合 `true` となる（同一Root IDで最初の数件がtrueとなる場合がある）|
|root_id|STRING|ページビューの中で発生したイベントを集約するための、ページビューイベントに対するユニークID|
|since_init_ms|INTEGER|SDKの初期化からの経過ミリ秒|
|since_prev_ms|INTEGER|直前のイベントからの経過ミリ秒|
|client_ip|STRING|訪問者のIPアドレス|
|user_agent|STRING|訪問者のUser-Agent|
|user_id|STRING|ウェブサイトにおけるユーザー識別のID（実装による。個人情報は扱うべきでない）|
|user_status|STRING|ウェブサイトにおけるユーザーの状態。ログインしているか否か、どういった権限を持つか等|
|user_attr|STRING|ユーザーに関する様々な追加情報を格納する枠。JSON文字列として記録されるので、BigQuery上ではJSON関数で展開して扱う|
|page_url|STRING|ウェブページのURL|
|page_referrer|STRING|リファラー（前のページのURL）|
|page_title|STRING|ウェブページのtitleタグの値|
|page_attr|STRING|ウェブページに関する追加情報（JSON文字列）|
|content_id|STRING|記事ID（BigQuery上で記事に関する情報とJOINするキーになることを想定）|
|content_headline|STRING|記事見出し（見出しが変化する場合に、実際に訪問者が目にした見出しを記録する）|
|content_status|STRING|記事の状態。ペイウォール等の見え方に影響する状態を記録することを想定|
|content_attr|STRING|記事に関する追加情報（情報量が多い場合はBigQueryでのJOINまたはDataflowを用いた拡張処理を推奨）|
|viewport_height|FLOAT|ビューポート（表示領域）の高さ|
|viewport_width|FLOAT|ビューポート（表示領域）の幅|
|screen_height|FLOAT|画面の高さ|
|screen_width|FLOAT|画面の幅|
|screen_orientation|STRING|画面の向き（機種が想定している定位置との関係に基づくため、縦長・横長といった意味は無い）|
|device_type|STRING|デバイスの種別|
|device_os|STRING|デバイスのOS|
|device_platform|STRING|デバイスのプラットフォーム|
|timing_interactive|INTEGER|RUMにおいてDOMが準備できるまでの所要時間（ミリ秒）|
|timing_dcl|INTEGER|RUMにおいてCSSOMまで準備できるまでの所要時間（ミリ秒）|
|timing_complete|INTEGER|RUMにおいて全てのサブリソースが準備できるまでの所要時間（ミリ秒）|
|timing_elapsed_ms|INTEGER|ページのロードを開始してからの経過時間（ミリ秒）|
|navigation_type|STRING|画面遷移の種別|
|navigation_redirect_count|INTEGER|画面遷移時のリダイレクト回数|
|page_height|FLOAT|ページの高さ（スクロール計測の基準となる）|
|scroll_depth|FLOAT|スクロール深度の具体的な値（割合またはピクセル数）|
|scroll_unit|STRING|スクロール深度の単位（PercentまたはPixels）|
|read_target_index|STRING|読了計測の対象の位置情報|
|read_target_id|STRING|読了計測の対象となったブロック要素のid属性|
|read_text_start_with|STRING|記事本文の冒頭部分の文字列|
|read_rate|FLOAT|読了率計測の基準となる可視領域の深さ（記事高が固定である前提で割合を算出）|
|read_text_length|FLOAT|記事本文として指定された要素中の文字数 ≒ 記事長 （正確性の点でCMSのデータを元にJOIN等するべき）|
|read_content_height|FLOAT|記事本文として指定された要素の高さ|
|read_attr|STRING|読了計測に関する追加情報|
|click_tag|STRING|クリックイベントの対象となったタグ|
|click_id|STRING|クリック対象のタグが持つid属性|
|click_class|STRING|クリック対象のタグが持つclass|
|click_path|STRING|data-trackableのヒエラルキーに基づく要素の位置情報|
|click_link|STRING|クリック対象がAタグの場合、その遷移先|
|click_text|STRING|リンクまたはボタンに表示されている文字列|
|click_attr|STRING|クリックに関する追加情報|
|media_src|STRING|メディア計測における、メディアのソースファイル|
|media_current_time|FLOAT|現在の再生地点（秒）|
|media_duration|FLOAT|メディア全体の長さ（秒）|
|media_played_percent|FLOAT|メディアで再生中の地点が全体の何パーセントに相当するか|
|media_attr|STRING|メディア計測に関する追加情報|
|form_name|STRING|フォーム計測の対象となるフォーム名|
|form_items|STRING|フォームに含まれる要素（JSON文字列）|
|form_first_item|STRING|フォームで最初に入力操作が行われた要素|
|form_last_item|STRING|フォームで最後に入力操作が行われた要素|
|form_started_since_init_ms|INTEGER|ページのロードからフォームの入力開始までの経過時間（ミリ秒）|
|form_ended_since_init_ms|INTEGER|ページのロードからフォームの入力を終えた時点までの経過時間（ミリ秒）|
|form_duration_ms|INTEGER|フォーム操作に要した時間（ミリ秒）|
|form_attr|STRING|フォーム計測に関する追加情報|
|campaign_code|STRING|広告計測に関する、トラッキングコード|
|campaign_name|STRING|広告計測に関する、utm_name互換枠|
|campaign_source|STRING|広告計測に関する、utm_source互換枠|
|campaign_medium|STRING|広告計測に関する、utm_medium互換枠|
|campaign_term|STRING|広告計測に関する、utm_term互換枠|
|campaign_content|STRING|広告計測に関する、utm_content互換枠|
|url_protocol|STRING|ページURLのパース結果。プロトコル部分|
|url_hostname|STRING|ページURLのパース結果。サブドメインを含むホスト名部分|
|url_pathname|STRING|ページURLのパース結果。パス部分|
|url_search|STRING|ページURLのパース結果。?以降のクエリーパラメータ全体|
|url_hash|STRING|ページURLのパース結果。#以降のハッシュ|
|url_query|STRING|ページURLのパース結果。クエリーパラメータをパースしkey:valとしたJSON文字列|
|referrer_protocol|STRING|リファラーURLのパース結果。プロトコル部分|
|referrer_hostname|STRING|リファラーURLのパース結果。サブドメインを含むホスト名部分|
|referrer_pathname|STRING|リファラーURLのパース結果。パス部分|
|referrer_search|STRING|リファラーURLのパース結果。?以降のクエリーパラメータ全体|
|referrer_hash|STRING|リファラーURLのパース結果。#以降のハッシュ|
|referrer_query|STRING|リファラーURLのパース結果。クエリーパラメータをパースしkey:valとしたJSON文字列|
|survey_name|STRING|Ingestly Surveyのアンケート名|
|survey_result|STRING|Ingestly Surveyのアンケート結果|
|o2o_name|STRING|Ingestly O2O のデータ連携名|
|o2o_scanner|STRING|Ingestly O2O でスキャンした側の情報（JSON文字列）|
|o2o_key|STRING|Ingestly O2O の真性検証用キー|
|o2o_result|STRING|Ingestly O2O で読み取った来場者情報|
|custom_attr|STRING|他の*_attr枠に収まらない任意の情報を格納する枠|
|is_tls|BOOLEAN|TLS通信か否か|
|is_ipv6|BOOLEAN|IPv6での通信か否か|
|request_accept_language|STRING|ブラウザの言語設定|
|request_accept_charset|STRING|ブラウザの文字コード設定|
|request_referer|STRING|ビーコンのリファラー。計測されたページ（デバッグ用途）|
|geo_continent_code|STRING|IPアドレスに基づく大陸コード|
|geo_region|STRING|IPアドレスに基づく地域|
|geo_country_name|STRING|IPアドレスに基づく国名|
|geo_country_code|STRING|IPアドレスに基づく国コード|
|geo_city|STRING|IPアドレスに基づく都市名|
|geo_latitude|FLOAT|IPアドレスに基づく代表地点の緯度|
|geo_longitude|FLOAT|IPアドレスに基づく代表地点の経度|
|geo_gmt_offset|STRING|IPアドレスに基づく地点のGMTとの時差|
|geo_conn_speed|STRING|回線の通信速度|
|server_datacenter|STRING|Fastlyエッジサーバーのデータセンター|
|server_region|STRING|Fastlyエッジサーバーの地域|
