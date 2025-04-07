:: ✅ INSTALL DEPENDENCIES
pip install flask kafka-python

:: ✅ START ZOOKEEPER (keep this running in a separate terminal)
cd C:\kafka\bin\windows
start zookeeper-server-start.bat ..\..\config\zookeeper.properties

:: ✅ START KAFKA SERVER (keep this running in another terminal)
cd C:\kafka\bin\windows
start kafka-server-start.bat ..\..\config\server.properties

:: ✅ CREATE KAFKA TOPIC (optional - skip if already created)
cd C:\kafka\bin\windows
kafka-topics.bat --create --topic orders --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

:: ✅ RUN FLASK WEB APP (click 'Produce Data' button in UI)
cd C:\Dhanush\realmonitor
python app.py

:: ✅ RUN KAFKA PRODUCER TO SEND FAKE ORDER DATA
cd C:\Dhanush\realmonitor
python producer.py

:: ✅ RUN KAFKA CONSUMER TO READ ORDER DATA
cd C:\Dhanush\realmonitor
python consumer.py
