# Finding certain messages in your WhatsApp message is sometimes hard, but Pandas makes it easier. Doesn't require root access!

##### Tested with Google Pixel 6 / Windows 10 / Python 3.9.13

```python
pip install a-pandas-ex-whatsapp-to-df
```

## Follow these steps if you want to avoid rooting your cell phone:

* Open WhatsApp on your Android device.
* Tap the three-dot overflow menu button and navigate to "Settings > Chats > Chat backup".
* Tap End-to-end encrypted backup, then tap "Turn on".
* Create a 64-digit key and save it! You will need it! DON'T CREATE a password!
* Tap Create and wait for WhatsApp to create an encrypted backup.
* Copy the backup from your Android device to your computer (File path on my device: storage/emulated/0/Android/media/com.whatsapp/WhatsApp/Databases/msgstore.db.crypt15  - You can localize the file using https://pypi.org/project/a-pandas-ex-adb-to-df )


```python
from a_pandas_ex_whatsapp_to_df import pd_add_whatsapp_to_df, decrypt_file
import pandas as pd
pd_add_whatsapp_to_df()

encrypteddb = r"F:\w32\Databases1\msgstore.db.crypt15"
decrypteddb = r"F:\newtest\msgstorexxxxxxxxxxxxxxxxx.db"
decryptkey = "THE 64-DIGIT KEY THAT YOU HAVE CREATED"


# this function will decrypt your WhatsApp database
# using https://github.com/ElDavoo/WhatsApp-Crypt14-Crypt15-Decrypter
# if the folder  WhatsApp-Crypt14-Crypt15-Decrypter doesn't exist, 
# the script will execute 
# "git clone https://github.com/ElDavoo/WhatsApp-Crypt14-Crypt15-Decrypter.git" 
# which means git must be installed and added to the path variable.
decrypt_file(
    encrypteddb, decrypteddb, decryptkey,
) 



df = pd.Q_whatsapp_to_df(sql_database=decrypteddb)

#output:
[I] Crypt15 / Raw key loaded
[I] Database header parsed
[I] Done
message_template 59
message_template_button 56
message_location 85
message_quoted_location 16
message_mentions 5377
message_media 99775
message_vcard 561
message_vcard_jid 529
message_streaming_sidecar 370
message_quoted_media 18289
message_quoted 114225
message_quoted_mentions 3088
message_thumbnail 60438
message_link 23190
message_quoted_vcard 73
message_text 12181
message_quoted_text 2077
message_send_count 56992
receipt_device 78638
message_system 21142
message_system_group 13739
message_system_value_change 2416
message_system_number_change 1660
message_system_photo_change 48
message_system_chat_participant 8134
receipt_user 359648
message_revoked 5151
messages_hydrated_four_row_template 59
message_system_block_contact 1
message_ephemeral_setting 33
message_view_once_media 13
mms_thumbnail_metadata 74
message_system_initial_privacy_provider 3304
message_privacy_state 15
message_system_business_state 18
message_ephemeral 37
played_self_receipt 204
message_system_linked_group_call 10
audio_data 6809
...


#You should get a DataFrame containing the following columns:

['_id_x',
 'chat_row_id',
 'from_me',
 'key_id',
 'sender_jid_row_id',
 'status',
 'broadcast',
 'recipient_count',
 'participant_hash',
 'origination_flags',
 'origin',
 'timestamp',
 'received_timestamp',
 'receipt_server_timestamp',
 'message_type',
 'text_data',
 'starred',
 'lookup_tables',
 'sort_id',
 'message_add_on_flags',
 '_id_y',
 'key_remote_jid',
 'remote_resource',
 'receipt_device_timestamp',
 'read_device_timestamp',
 'played_device_timestamp',
 'phone_number',
 'user_id',
 '_id',
 'user',
 'server',
 'agent',
 'type',
 'raw_string',
 'device',
 'group',
 'message_row_id',
 'video_call',
 'group_jid_row_id',
 'is_joinable_group_call',
 'conversation__id',
 'conversation_jid_row_id',
 'conversation_hidden',
 'conversation_subject',
 'conversation_created_timestamp',
 'conversation_display_message_row_id',
 'conversation_last_message_row_id',
 'conversation_last_read_message_row_id',
 'conversation_last_read_receipt_sent_message_row_id',
 'conversation_last_important_message_row_id',
 'conversation_archived',
 'conversation_sort_timestamp',
 'conversation_mod_tag',
 'conversation_gen',
 'conversation_spam_detection',
 'conversation_unseen_earliest_message_received_time',
 'conversation_unseen_message_count',
 'conversation_unseen_missed_calls_count',
 'conversation_unseen_row_count',
 'conversation_plaintext_disabled',
 'conversation_vcard_ui_dismissed',
 'conversation_change_number_notified_message_row_id',
 'conversation_show_group_description',
 'conversation_ephemeral_expiration',
 'conversation_last_read_ephemeral_message_row_id',
 'conversation_ephemeral_setting_timestamp',
 'conversation_unseen_important_message_count',
 'conversation_ephemeral_disappearing_messages_initiator',
 'conversation_group_type',
 'conversation_last_message_reaction_row_id',
 'conversation_last_seen_message_reaction_row_id',
 'conversation_unseen_message_reaction_count',
 'conversation_growth_lock_level',
 'conversation_growth_lock_expiration_ts',
 'conversation_last_read_message_sort_id',
 'conversation_display_message_sort_id',
 'conversation_last_message_sort_id',
 'conversation_last_read_receipt_sent_message_sort_id',
 'message_forwarded',
 'message_template_message_row_id',
 'message_template_content_text_data',
 'message_template_footer_text_data',
 'message_template_template_id',
 'message_template_csat_trigger_expiration_ts',
 'message_template_button__id',
 'message_template_button_message_row_id',
 'message_template_button_text_data',
 'message_template_button_extra_data',
 'message_template_button_button_type',
 'message_template_button_used',
 'message_template_button_selected_index',
 'message_template_button_otp_button_type',
 'message_location_message_row_id',
 'message_location_chat_row_id',
 'message_location_latitude',
 'message_location_longitude',
 'message_location_place_name',
 'message_location_place_address',
 'message_location_url',
 'message_location_live_location_share_duration',
 'message_location_live_location_sequence_number',
 'message_location_live_location_final_latitude',
 'message_location_live_location_final_longitude',
 'message_location_live_location_final_timestamp',
 'message_location_map_download_status',
 'message_quoted_location_message_row_id',
 'message_quoted_location_latitude',
 'message_quoted_location_longitude',
 'message_quoted_location_place_name',
 'message_quoted_location_place_address',
 'message_quoted_location_url',
 'message_quoted_location_thumbnail',
 'message_mentions__id',
 'message_mentions_message_row_id',
 'message_mentions_jid_row_id',
 'message_media_message_row_id',
 'message_media_chat_row_id',
 'message_media_autotransfer_retry_enabled',
 'message_media_multicast_id',
 'message_media_media_job_uuid',
 'message_media_transferred',
 'message_media_transcoded',
 'message_media_file_path',
 'message_media_file_size',
 'message_media_suspicious_content',
 'message_media_trim_from',
 'message_media_trim_to',
 'message_media_face_x',
 'message_media_face_y',
 'message_media_media_key',
 'message_media_media_key_timestamp',
 'message_media_width',
 'message_media_height',
 'message_media_has_streaming_sidecar',
 'message_media_gif_attribution',
 'message_media_thumbnail_height_width_ratio',
 'message_media_direct_path',
 'message_media_first_scan_sidecar',
 'message_media_first_scan_length',
 'message_media_message_url',
 'message_media_mime_type',
 'message_media_file_length',
 'message_media_media_name',
 'message_media_file_hash',
 'message_media_media_duration',
 'message_media_page_count',
 'message_media_enc_file_hash',
 'message_media_partial_media_hash',
 'message_media_partial_media_enc_hash',
 'message_media_is_animated_sticker',
 'message_media_original_file_hash',
 'message_media_mute_video',
 'message_vcard__id',
 'message_vcard_message_row_id',
 'message_vcard_vcard',
 'message_vcard_jid__id',
 'message_vcard_jid_vcard_jid_row_id',
 'message_vcard_jid_vcard_row_id',
 'message_vcard_jid_message_row_id',
 'message_streaming_sidecar_message_row_id',
 'message_streaming_sidecar_sidecar',
 'message_streaming_sidecar_chunk_lengths',
 'message_streaming_sidecar_timestamp',
 'message_quoted_media_message_row_id',
 'message_quoted_media_media_job_uuid',
 'message_quoted_media_transferred',
 'message_quoted_media_file_path',
 'message_quoted_media_file_size',
 'message_quoted_media_media_key',
 'message_quoted_media_media_key_timestamp',
 'message_quoted_media_width',
 'message_quoted_media_height',
 'message_quoted_media_direct_path',
 'message_quoted_media_message_url',
 'message_quoted_media_mime_type',
 'message_quoted_media_file_length',
 'message_quoted_media_media_name',
 'message_quoted_media_file_hash',
 'message_quoted_media_media_duration',
 'message_quoted_media_page_count',
 'message_quoted_media_enc_file_hash',
 'message_quoted_media_thumbnail',
 'message_quoted_message_row_id',
 'message_quoted_chat_row_id',
 'message_quoted_parent_message_chat_row_id',
 'message_quoted_from_me',
 'message_quoted_sender_jid_row_id',
 'message_quoted_key_id',
 'message_quoted_timestamp',
 'message_quoted_message_type',
 'message_quoted_text_data',
 'message_quoted_payment_transaction_id',
 'message_quoted_lookup_tables',
 'message_quoted_origin',
 'message_quoted_mentions__id',
 'message_quoted_mentions_message_row_id',
 'message_quoted_mentions_jid_row_id',
 'message_thumbnail_message_row_id',
 'message_thumbnail_thumbnail',
 'message_link__id',
 'message_link_chat_row_id',
 'message_link_message_row_id',
 'message_link_link_index',
 'message_quoted_vcard__id',
 'message_quoted_vcard_message_row_id',
 'message_quoted_vcard_vcard',
 'message_text_message_row_id',
 'message_text_description',
 'message_text_page_title',
 'message_text_url',
 'message_text_font_style',
 'message_text_text_color',
 'message_text_background_color',
 'message_text_preview_type',
 'message_text_invite_link_group_type',
 'message_quoted_text_message_row_id',
 'message_quoted_text_thumbnail',
 'message_send_count_message_row_id',
 'message_send_count_send_count',
 'receipt_device__id',
 'receipt_device_message_row_id',
 'receipt_device_receipt_device_jid_row_id',
 'receipt_device_receipt_device_timestamp',
 'receipt_device_primary_device_version',
 'message_system_message_row_id',
 'message_system_action_type',
 'message_system_group_message_row_id',
 'message_system_group_is_me_joined',
 'message_system_value_change_message_row_id',
 'message_system_value_change_old_data',
 'message_system_number_change_message_row_id',
 'message_system_number_change_old_jid_row_id',
 'message_system_number_change_new_jid_row_id',
 'message_system_photo_change_message_row_id',
 'message_system_photo_change_new_photo_id',
 'message_system_photo_change_old_photo',
 'message_system_photo_change_new_photo',
 'message_system_chat_participant_message_row_id',
 'message_system_chat_participant_user_jid_row_id',
 'receipt_user__id',
 'receipt_user_message_row_id',
 'receipt_user_receipt_user_jid_row_id',
 'receipt_user_receipt_timestamp',
 'receipt_user_read_timestamp',
 'receipt_user_played_timestamp',
 'message_revoked_message_row_id',
 'message_revoked_revoked_key_id',
 'message_revoked_admin_jid_row_id',
 'messages_hydrated_four_row_template_message_row_id',
 'messages_hydrated_four_row_template_message_template_id',
 'message_ephemeral_setting_message_row_id',
 'message_ephemeral_setting_setting_duration',
 'message_ephemeral_setting_setting_reason',
 'message_ephemeral_setting_user_jid_row_id_csv',
 'message_view_once_media_message_row_id',
 'message_view_once_media_state',
 'mms_thumbnail_metadata_message_row_id',
 'mms_thumbnail_metadata_direct_path',
 'mms_thumbnail_metadata_media_key',
 'mms_thumbnail_metadata_media_key_timestamp',
 'mms_thumbnail_metadata_enc_thumb_hash',
 'mms_thumbnail_metadata_thumb_hash',
 'mms_thumbnail_metadata_thumb_width',
 'mms_thumbnail_metadata_thumb_height',
 'mms_thumbnail_metadata_transferred',
 'mms_thumbnail_metadata_micro_thumbnail',
 'mms_thumbnail_metadata_insert_timestamp',
 'message_system_initial_privacy_provider_message_row_id',
 'message_system_initial_privacy_provider_privacy_provider',
 'message_system_initial_privacy_provider_verified_biz_name',
 'message_system_initial_privacy_provider_biz_state_id',
 'message_privacy_state_message_row_id',
 'message_privacy_state_host_storage',
 'message_privacy_state_actual_actors',
 'message_privacy_state_privacy_mode_ts',
 'message_privacy_state_business_name',
 'message_system_business_state_message_row_id',
 'message_system_business_state_privacy_message_type',
 'message_system_business_state_business_name',
 'message_ephemeral_message_row_id',
 'message_ephemeral_duration',
 'message_ephemeral_expire_timestamp',
 'message_ephemeral_keep_in_chat',
 'played_self_receipt_message_row_id',
 'played_self_receipt_to_jid_row_id',
 'played_self_receipt_participant_jid_row_id',
 'played_self_receipt_message_id',
 'message_system_linked_group_call_message_row_id',
 'message_system_linked_group_call_call_id',
 'message_system_linked_group_call_is_video_call',
 'audio_data_message_row_id',
 'audio_data_waveform']


         _id_x  ...                                audio_data_waveform
0         2101  ...                                                NaN
1       517004  ...                                                NaN
2       441187  ...                                                NaN
3       441119  ...                                                NaN
4       441115  ...                                                NaN
        ...  ...                                                ...
866976  803337  ...                                                NaN
866977  803333  ...  b'\x00\x00F\x00\x00\x14%\x1c\x004\x00\x00\r\x1...
866978  803332  ...                                                NaN
866979  803331  ...  b'\x00\x00\x00\x008\x06&;*\x00\x00\x16\x1178)\...
866980  803330  ...                                                NaN
[866981 rows x 292 columns]

```

## If this is too much information, you can exclude tables from being parsed

```python
Parameters:
	sql_database: str
		The file path to your decrypted SQL Database
	databases_to_add: tuple
		The SQL tables to include in the output DataFrame
		default = (
		"message_template",
		"message_template_button",
		"message_location",
		"message_quoted_location",
		"message_mentions",
		"message_media",
		"message_vcard",
		"message_vcard_jid",
		"message_streaming_sidecar",
		"message_quoted_media",
		"message_quoted",
		"message_quoted_mentions",
		"message_thumbnail",
		"message_link",
		"message_quoted_vcard",
		"message_text",
		"message_quoted_text",
		"message_send_count",
		"receipt_device",
		"message_system",
		"message_system_group",
		"message_system_value_change",
		"message_system_number_change",
		"message_system_photo_change",
		"message_system_chat_participant",
		"receipt_user",
		"message_revoked",
		"messages_hydrated_four_row_template",
		"message_system_block_contact",
		"message_ephemeral_setting",
		"message_view_once_media",
		"mms_thumbnail_metadata",
		"message_system_initial_privacy_provider",
		"message_privacy_state",
		"message_system_business_state",
		"message_ephemeral",
		"played_self_receipt",
		"message_system_linked_group_call",
		"audio_data",
		)
	optimize_dtypes:bool
		Optimize dtypes at the end of the conversion to save memory
		default = True
Returns
	df: pd.DataFrame

```
