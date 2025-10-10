# Gaialith Custom Newsletter System

This project uses a custom email subscription system that sends emails directly to your Mailchimp account via Zapier webhook integration.

## Features

- ✅ Custom popup form (no redirect to Mailchimp)
- ✅ Client-side email validation
- ✅ Zapier webhook integration with Mailchimp
- ✅ Better user experience with loading states
- ✅ No server setup required
- ✅ Automatic duplicate handling via Zapier

## How It Works

1. **User Experience**: User clicks "Join Our Mailing List" → custom popup appears
2. **Form Submission**: User enters email → form sends data to Zapier webhook
3. **Zapier Processing**: Zapier receives the webhook and adds subscriber to Mailchimp
4. **Response**: User sees success message immediately

## Setup Instructions

### 1. Zapier Configuration

Your Zapier webhook is already configured at:
```
https://hooks.zapier.com/hooks/catch/24936259/u5dshlp/
```

Make sure your Zapier zap is set up to:
- **Trigger**: Webhooks by Zapier (Catch Hook)
- **Action**: Mailchimp (Add Subscriber to List)

### 2. Test the System

1. Open your `index.html` file in a web browser
2. Click "Join Our Mailing List"
3. Enter an email address and submit
4. Check your Mailchimp audience to confirm the subscription

### 3. Data Format

The webhook sends this data structure:
```json
{
  "email": "user@example.com",
  "timestamp": "2024-01-15T10:30:00.000Z",
  "source": "gaialith-website"
}
```

## Zapier Setup Details

### Webhook Configuration
- **URL**: `https://hooks.zapier.com/hooks/catch/24936259/u5dshlp/`
- **Method**: POST
- **Content-Type**: application/json

### Mailchimp Action Settings
- **List**: Your Mailchimp audience
- **Email Address**: Map from webhook `email` field
- **Status**: Subscribed
- **Additional Fields**: Map `timestamp` and `source` if needed

## Benefits of Zapier Approach

- **No Server Required**: Works with static hosting (GitHub Pages, Netlify, etc.)
- **Reliable**: Zapier handles retries and error handling
- **Scalable**: No server maintenance or scaling concerns
- **Easy Setup**: Visual interface for configuration
- **Monitoring**: Built-in Zapier monitoring and logs

## Troubleshooting

### Common Issues

1. **Webhook not triggering**: Check Zapier zap status and test the webhook
2. **CORS errors**: Zapier webhooks handle CORS automatically
3. **Duplicate subscriptions**: Zapier can be configured to handle duplicates

### Testing Your Webhook

You can test your webhook directly using curl:
```bash
curl -X POST https://hooks.zapier.com/hooks/catch/24936259/u5dshlp/ \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","timestamp":"2024-01-15T10:30:00.000Z","source":"test"}'
```

### Zapier Monitoring

- Check your Zapier dashboard for zap runs
- Monitor webhook delivery status
- Review any error logs in Zapier

## Deployment

Since this uses Zapier webhooks, you can deploy your site to any static hosting service:

- **GitHub Pages**: Free static hosting
- **Netlify**: Easy deployment with custom domains
- **Vercel**: Fast global CDN
- **Firebase Hosting**: Google's hosting platform

No server configuration needed!

## Security Notes

- Webhook URL is public (this is normal for Zapier)
- Email validation happens on the client side
- Zapier handles the secure connection to Mailchimp
- No sensitive data stored in your code

## Support

If you encounter issues:
1. Check Zapier zap status and logs
2. Test the webhook URL directly
3. Verify Mailchimp integration in Zapier
4. Check browser console for JavaScript errors
