# TalkingData AdTracking Fraud Detection Challenge

## Overview
Fraud risk is everywhere, but for companies that advertise online, click fraud can happen at an overwhelming volume, resulting in misleading click data and wasted money. Ad channels can drive up costs by simply clicking on the ad at a large scale. With over 1 billion smart mobile devices in active use every month, China is the largest mobile market in the world and therefore suffers from huge volumes of fradulent traffic.

## Data
Data aquisition from kaggle competion: https://www.kaggle.com/c/talkingdata-adtracking-fraud-detection/data

## Feature Engieering
Added time features: hour, min, sec, day, weekday, day of year, month
Added count features: Count channl for ip-app,  Count channel for ip-app-os, Count channel for ip-app-device, Count channel for ip-day-hour, Count channel for ip-app-day-hour, Count channl for ip-app-device-day-hour, Popularity of app / channel 
Added Variance features:  Variance in day for ip-app-channel, Variance in day for ip-app-device, Variance in day for ip-app-os
Added Mean features:  Mean hour for ip-app-channel
Added unique features

## ML Model
* Features = ['ip', 'app', 'device', 'os', 'channel', 'hour', 'minute', 'second', 'day', 'weekday', 'dayofyear', 'month', 'prev_identical_clicks', 'future_identical_clicks', 'ip_app_count_channel', 'ip_app_os_count_channel', 'ip_app_device_count_channel',
 'ip_day_hour_count_channel', 'ip_app_day_hour_count_channel', 'ip_app_device_day_hour_count_channel', 'app_count_channel', 'channel_count_app', 'ip_app_channel_var_day', 'ip_app_device_var_day', 'ip_app_os_var_day', 'ip_app_channel_mean_hour', 'ip_nunique_channel', 'ip_nunique_app', 'ip_day_nunique_hour', 'ip_app_nunique_os', 'ip_nunique_device', 'app_nunique_channel', 'ip_device_os_nunique_app']
* XGBOOST: 96.74%
* XGBClassifier(
          learning_rate = 0.1,
          max_depth = 4, 
          n_estimators=200,
          subsample=0.6,
          reg_alpha = 4,
          n_jobs = 4,
          objective='binary:logistic')
* LightBGM: 95.69%
* LGBMClassifier(
        boosting_type='gbdt', 
        max_depth=2, 
        learning_rate=0.1, 
        n_estimators=200, 
        subsample=0.6,
        objective = 'binary',
        metric = 'auc'
        )

## Future Intrerests
* Subsampling, Undersampling, Oversampling to get rid of data imbalance
* Do more feature engineering to find better features
