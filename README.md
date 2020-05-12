# aws-psycopg2
Follow these steps to use Pyscopg2 in your AWS Lambda Function (Lambda Layer)

1. Create a new directory:
mkdir aws-psycopg2

2. Change directory
cd aws-psycopg2

3. Create a script named get_layer_packages.sh
vi get_layer_packages.sh

4. Enter the following code in the get_layer_packages.sh

export PKG_DIR="python"

rm -rf ${PKG_DIR} && mkdir -p ${PKG_DIR}

docker run --rm -v $(pwd):/foo -w /foo lambci/lambda:build-python3.6 \
    pip install -r requirements.txt --no-deps -t ${PKG_DIR}
 
5. Create requirements.txt
vi requirements.txt

6. Add aws-psycopg2 to requirements.txt
aws-psycopg2

7. Change permission
chmod +x get_layer_packages.sh

8. Run script
./get_layer_packages.sh

9. Zip
zip -r aws-psycopg2.zip .

10. Upload this zip file to AWS lambda as Layer.
11. in your lambda function, just use:
import psycopg2

12. Happy coding.. :)
