MixpanelClient
===================

Basic Mixpanel iOS client to export data via the Mixpanel API using your API key and secret.

The code follows the Mixpanel documentation as close as possible, so naming and parameters are exactly as shown.

[Visit API documentation](https://mixpanel.com/docs/api-documentation/data-export-api)

The project includes a Podspec file for [AFNetworking](https://github.com/AFNetworking/AFNetworking), so make sure to run the installation for that library.

### Initialisations

    - (MixpanelClient *)initWithDelegate:(NSObject *)newDelegate;

### Setting authentication details

    - (void)setApiKey:(NSString *)key andSecret:(NSString *)secret;

### Delegates

There are just three methods that by adding `MixpanelClientDelegate` will allow you to use in your controllers. This returns any data that is received from the server:

#### requestSucceededForMethod:(NSString *)method

    - (void)requestSucceededForMethod:(NSString *)method
    {
        NSLog(@"The method %@ was successful.", method);
    }

#### requestFailedWithError:(NSError *)error

    - (void)requestFailedWithError:(NSError *)error
    {
        NSLog(@"An error occurred: %@", [error debugDescription]);
    }

#### @optional receivedData:(id)data

    - (void)receivedData:(id)data
    {
        // Data is either an NSDictionary or an NSArray
        NSLog(@"Data was received: %@", data);
    }

### Events

    /*
    METHOD: events
    URI: http://mixpanel.com/api/2.0/events/
    Parameters:
    'event'        NSArray
    'type'         NSString
    'unit'         NSString
    'interval'     NSInteger
    'format'       NSString
    */

    - (void)events:(NSDictionary *)params;

#### events/top

    /*
    METHOD: events/top
    URI: http://mixpanel.com/api/2.0/events/top/
    Parameters:
    'type'         NSString
    'limit'        NSInteger
    */

    - (void)eventsTop:(NSDictionary *)params;

#### events/names

    /*
    METHOD: events/names
    URI: http://mixpanel.com/api/2.0/events/names/
    Parameters:
    'type'         NSString
    'limit'        NSInteger
    */

    - (void)eventsNames:(NSDictionary *)params;

#### events/properties

    /*
    METHOD: events/properties
    URI: http://mixpanel.com/api/2.0/events/properties/
    Parameters:
    'event'        NSString
    'name'         NSString
    'values'       NSArray
    'type'         NSString
    'unit'         NSString
    'interval'     NSInteger
    'format'       NSString
    'limit'        NSInteger
    */

    - (void)eventsProperties:(NSDictionary *)params;

#### events/properties/top

    /*
    METHOD: events/properties/top
    URI: http://mixpanel.com/api/2.0/events/properties/top/
    Parameters:
    'event'        NSString
    'limit'        NSInteger
    */

    - (void)eventsPropertiesTop:(NSDictionary *)params;

#### events/properties/values

    /*
    METHOD: events/properties/values
    URI: http://mixpanel.com/api/2.0/events/properties/values/
    Parameters:
    'event'        NSString
    'name'         NSString
    'limit'        NSInteger
    'bucket'       NSString
    */

    - (void)eventsPropertiesValues:(NSDictionary *)params;

### Funnels

    /*
    METHOD: funnels
    URI: http://mixpanel.com/api/2.0/funnels/
    Parameters:
    'funnel_id'    NSInteger
    'from_date'    NSString
    'to_date'      NSString
    'length'       NSInteger
    'interval'     NSInteger
    'unit'         NSString
    'on'           NSString
    'where'        NSString
    'limit         NSInteger
    */

    - (void)funnels:(NSDictionary *)params;

#### funnels/list

    /*
    METHOD: funnels/list
    URI: http://mixpanel.com/api/2.0/funnels/list/
    */

    - (void)funnelsList;

### Segmentation

    /*
    METHOD: segmentation
    URI: http://mixpanel.com/api/2.0/segmentation/
    Parameters:
    'event'        NSString
    'from_date'    NSString
    'to_date'      NSString
    'on'           NSString
    'unit'         NSString
    'where'        NSString
    'limit'        NSInteger
    'type'         NSString
    */

    - (void)segmentation:(NSDictionary *)params;

#### segmentation/numeric

    /*
    METHOD: segmentation/numeric
    URI: http://mixpanel.com/api/2.0/segmentation/numeric/
    Parameters:
    'event'        NSString
    'from_date'    NSString
    'to_date'      NSString
    'on'           NSString
    'buckets'      NSInteger
    'unit'         NSString
    'where'        NSString
    'type'         NSString
    */

    - (void)segmentationNumeric:(NSDictionary *)params;

#### segmentation/sum

    /*
    METHOD: segmentation/sum
    URI: http://mixpanel.com/api/2.0/segmentation/sum/
    Parameters:
    'event'        NSString
    'from_date'    NSString
    'to_date'      NSString
    'on'           NSString
    'unit'         NSString
    'where'        NSString
    */

    - (void)segmentationSum:(NSDictionary *)params;

#### segmentation/average

    /*
    METHOD: segmentation/average
    URI: http://mixpanel.com/api/2.0/segmentation/average/
    Parameters:
    'event'        NSString
    'from_date'    NSString
    'to_date'      NSString
    'on'           NSString
    'unit'         NSString
    'where'        NSString
    */

    - (void)segmentationAverage:(NSDictionary *)params;

### Retention

    /*
    METHOD: retention
    URI: http://mixpanel.com/api/2.0/retention/
    Parameters:
    'from_date'        NSString
    'to_date'          NSString
    'retention_type'   NSString
    'born_event'       NSString
    'event'            NSString
    'born_where'       NSString
    'where'            NSString
    'interval'         NSInteger
    'interval_count'   NSInteger
    'unit'             NSString
    'on'               NSString
    'limit'            NSInteger
    */

    - (void)retention:(NSDictionary *)params;

### Engage

    /*
    METHOD: engage
    URI: http://mixpanel.com/api/2.0/engage/
    Parameters:
    'where'        NSString
    'session_id'   NSString
    'page'         NSInteger
    */

    - (void)engage:(NSDictionary *)params;
