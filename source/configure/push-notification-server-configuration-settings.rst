:orphan:
:nosearch:

Configure Mattermost to enable push notifications to Mattermost clients by going to **System Console > Environment > Push Notification Server**, or by editing the ``config.json`` file as described in the following tables. Changes to configuration settings in this section require a server restart before taking effect.

.. config:setting:: push-enablenotifications
  :displayname: Enable push notifications (Push Notifications)
  :systemconsole: Environment > Push Notification Server
  :configjson: .EmailSettings.SendPushNotifications
  :environment: MM_EMAILSETTINGS_SENDPUSHNOTIFICATIONS

  - **true**: **(Default)** Your Mattermost server sends mobile push notifications.
  - **false**: Mobile push notifications are disabled.

Enable push notifications
~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

 <p class="mm-label-note">Also available in legacy Mattermost Enterprise Edition E10 or E20</p>

+------------------------------------------------------------------+--------------------------------------------------------------------------------+
| Enable or disable Mattermost push notifications.                 | - System Config path: **Environment > Push Notification Server**               |
|                                                                  | - ``config.json setting``: ``".EmailSettings.SendPushNotifications": true",``  |
| - **Do not send push notifications**: Mobile push notifications  | - Environment variable: ``MM_EMAILSETTINGS_SENDPUSHNOTIFICATIONS``             |
|   are disabled.                                                  |                                                                                |
| - **Use HPNS connection with uptime SLA to send notifications    |                                                                                |
|   to iOS and Android apps**: **(Default)** Use Mattermost's      |                                                                                |
|   hosted push notification service.                              |                                                                                |
| - **Use TPNS connection to send notifications to iOS and         |                                                                                |
|   Android apps**: Use Mattermost's test push notification        |                                                                                |
|   service.                                                       |                                                                                |
| - **Manually enter Push Notification Service location**:         |                                                                                |
|   When building your own custom mobile apps, you must host your  |                                                                                |
|   own mobile push proxy service, and specify that URL in the     |                                                                                |
|   **Push Notification Server** field.                            |                                                                                |
+------------------------------------------------------------------+--------------------------------------------------------------------------------+
| **Notes**:                                                                                                                                        |
|                                                                                                                                                   |
| - Mattermost Enterprise, Professional, and Cloud customers can use Mattermost’s SLA-bound :ref:`Hosted Push Notification Service (HPNS)           |
|   <deploy/mobile-hpns:hosted push notifications service (hpns)>` in one of two locations, including the United States and Germany.                |
|   Mattermost Team Edition customers can use Mattermost's                                                                                          |
|   :ref:`Test Push Notification server (TPNS) <deploy/mobile-hpns:test push notifications service (tpns)>`.                                        |
| - The TPNS is provided for testing push notifications prior to compiling your own service, and isn't available for Mattermost Cloud deployments.  |
|   Ensure you’re familiar with its limitations.                                                                                                    |
| - Review the :doc:`mobile push notifications </deploy/mobile-hpns>` and :doc:`mobile apps </deploy/build-custom-mobile-apps>` documentation,      |
|   including guidance on compiling your own mobile apps and MPNS, before deploying to production.                                                  |
| - See the :ref:`documentation <deploy/mobile-hpns:host your own push proxy service>` for details on hosting your own push proxy service.          |
| - To confirm push notifications are working, connect to the `Mattermost iOS App <https://apps.apple.com/us/app/mattermost/id1257222717>`__        |
|   available on the App Store, or the `Mattermost Android App <https://play.google.com/store/apps/details?id=com.mattermost.rn>`__ available on    |
|   Google Play.                                                                                                                                    |
+-----------------------------------------------------------------+---------------------------------------------------------------------------------+

.. config:setting:: push-serverlocation
  :displayname: Push notification server location (Push Notifications)
  :systemconsole: Environment > Push Notification Server
  :configjson: .EmailSettings.PushNotificationServer
  :environment: MM_EMAILSETTINGS_PUSHNOTIFICATIONSERVER
  :description: The physical location of the Mattermost Hosted Notification Service (HPNS) server.

Push notification server location
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

 <p class="mm-label-note">Also available in legacy Mattermost Enterprise Edition E10 or E20</p>

+-----------------------------------------------------------------+--------------------------------------------------------------------------------+
| The physical location of the Mattermost Hosted Push             | - System Config path: **Environment > Push Notification Server**               |
| Notification Service (HPNS) server.                             | - ``config.json setting``: ``".EmailSettings.PushNotificationServer",``        |
|                                                                 | - Environment variable: ``MM_EMAILSETTINGS_PUSHNOTIFICATIONSERVER``            |
| Select from **US** **(Default)** or **Germany** to              |                                                                                |
| automatically populate the **Push Notification Server**         |                                                                                |
| field server URL.                                               |                                                                                |
+-----------------------------------------------------------------+--------------------------------------------------------------------------------+

.. config:setting:: push-maxnotificationsperchannel
  :displayname: Maximum notifications per channel (Push Notifications)
  :systemconsole: Environment > Push Notification Server
  :configjson: .TeamSettings.MaxNotificationsPerChannel
  :environment: MM_EMAILSETTINGS_MAXNOTIFICATIONSPERCHANNEL
  :description: The maximum total number of users in a channel before @all, @here, and @channel no longer send desktop, email, or mobile push notifications to maximize performance. Default is **1000** users.

Maximum notifications per channel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

 <p class="mm-label-note">Also available in legacy Mattermost Enterprise Edition E10 or E20</p>

+-----------------------------------------------------------------+--------------------------------------------------------------------------------------+
| The maximum total number of users in a channel before @all,     | - System Config path: **Environment > Push Notification Server**                     |
| @here, and @channel no longer send desktop, email, or mobile    | - ``config.json setting``: ``".TeamSettings.MaxNotificationsPerChannel: 1000",``     |
| push notifications to maximize performance.                     | - Environment variable: ``MM_EMAILSETTINGS_MAXNOTIFICATIONSPERCHANNEL``              |
|                                                                 |                                                                                      |
| Numerical input. Default is **1000**.                           |                                                                                      |
+-----------------------------------------------------------------+--------------------------------------------------------------------------------------+
| **Note**: We recommend increasing this value a little at a time, monitoring system health by tracking :doc:`performance monitoring metrics             |
| </scale/deploy-prometheus-grafana-for-performance-monitoring>`, and only increasing this value if large channels have restricted permissions           |
| controlling who can post to the channel, such as a :ref:`read-only channel <onboard/advanced-permissions:read only channels>`.                         |
+-----------------------------------------------------------------+--------------------------------------------------------------------------------------+
