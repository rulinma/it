# EventSource

* JavaScript 代码

    ```javascript
       useEffect(() => {
        const eventSource = new EventSource('http://localhost:5005/api/sse/' + uid);
        eventSource.onmessage = (event) => {
            console.log(event.data);
        };
        return () => {
            eventSource.close();
        };
    }, []);
    ```

    ```javascript
    const eventSource = new EventSource('http://localhost:5005/api/sse/' + uid);

    eventSource.onmessage = (event) => {
        // console.log(event);
        console.log(event.data);
    };
    eventSource.close = () => {
        eventSource.close();
    };
    ```

* Flask 代码

    ```python
    @app.route('/api/sse/<uuid>', methods=['GET', 'POST'])
    def sse(uuid):
        logging.info(uuid)
    ```

* Java 代码

    ```java
    
    ```
