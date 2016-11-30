
# ringspeak

Ring a phone number (Twilio) and speak some text (Amazon Polly)

## SYNOPSIS

    ringspeak [--from-phone NUMBER] [--to-phone NUMBER] --say "text to speak"

## OPTIONS

    --from-phone NUMBER
      Twilio phone number to initiate the call

    --to-phone NUMBER
      Phone number to call

   --voice VOICE
      Amazon Polly Voice ID

    --say TEXT
      Text to speak. The [--say] flag is optional.

    --at ATSPEC
      Generate an "at" job with the specified options instead of
      making the call immediately.

## ENVIRONMENT

    RINGSPEAK_CONFIG
      [Optional] Location of setup script to source.
      Default: $HOME/.ringspeak
      Tip: Set up the below environment variables in this file!

    TWILIO_ACCOUNT_SID="..."
    TWILIO_AUTH_TOKEN="..."
      Twilio credentials

    RINGSPEAK_S3_BUCKET="..."
      [Optional] S3 bucket to hold voice audio files

    RINGSPEAK_S3_PREFIX="..."
      [Optional] S3 key prefix for audio files

    RINGSPEAK_FROM_PHONE="+1..."
      [Optional] Default Twilio phone number to initiate the call

    RINGSPEAK_TO_PHONE="+1..."
      [Optional] Default phone number to call

    These can also be useful:
    export AWS_CONFIG_FILE=...
    export AWS_DEFAULT_PROFILE=...

## EXAMPLES

Alert of a cron job failure

    ... || ringspeak --to +1NUMBER "Please review the cron job failure messages"

Scheduled wake up call

    ringspeak --at 6:30am \
      "Good morning!" \
      "Breakfast is being served now in Venetian Hall G.." \
      "Werners keynote is at 8:30."
