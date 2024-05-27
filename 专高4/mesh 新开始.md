1. 添加属性的标签 
	[RequireComponent(typeof(MeshFilter))] 通过此标签动态的为对象添加脚本
		使用属性标签`[RequireComponent]`而不是手动调用`AddComponent`有以下几个原因：

	1. 便捷性：通过使用属性标签，您可以在脚本的声明中直接指定所需的组件，而无需在脚本的逻辑中编写额外的代码来手动添加组件。这简化了脚本的编写和使用过程。
    
	2. 自动化：当您将带有属性标签的脚本附加到游戏对象上时，Unity会自动检查该对象是否具有所需的组件。如果缺少某个组件，Unity会自动将其添加到游戏对象上，减少了手动管理组件的工作量。
    
	3. 可读性和可维护性：属性标签可以直接在脚本的声明中看到并理解所需的组件。这提高了代码的可读性，使其他开发人员能够更轻松地理解脚本的功能和要求。此外，如果后续需要修改所需的组件，只需更改属性标签的声明，而无需在整个脚本中搜索和修改`AddComponent`的调用。

2.  如何生成mesh 网格 等等
	```c#
	这里用代码生成了一个正方行的面
		mesh = new Mesh();
        mesh.vertices = new Vector3[] { new Vector3(0, 0, 0), new Vector3(1, 0, 0), new Vector3(1, 1, 0), new Vector3(0, 1, 0) }; //设置网格顶点,v3是顶点的坐标  拥有下标
        mesh.triangles = new int[] { 2, 1, 0, 0, 3, 2 };    //绘制时的顺序(索引)  索引顺序会造成三角形朝向的改变(顺时针,逆时针)
        mesh.RecalculateNormals();//计算法线信息 (计算光照) 不然会不亮
        GetComponent<MeshFilter>().mesh = mesh;//获取组件并赋值网格
        Material mat = new Material(Shader.Find("Standard")); //创建材质球  Shader.Find("着色器的名字")

	这里是正方体
		mesh = new Mesh();
	    mesh.vertices = new Vector3[] { new Vector3(0, 0, 0), new Vector3(5, 0, 0), new Vector3(5, 0, 5), new Vector3(0, 0, 5) ,
                                         new Vector3(0, 5, 0), new Vector3(5, 5, 0), new Vector3(5, 5, 5), new Vector3(0, 5, 5) }; //设置网格顶点,v3是顶点的坐标  拥有下标
        mesh.triangles = new int[] { 0, 4, 5,   0, 5, 1,
                                     3 ,6 ,7,   3 ,2 ,6,
                                     0 ,3 ,7,   0 ,7 ,4,
                                     1 ,5 ,6,   2 ,1 ,6,
                                     1 ,3 ,0,   1 ,2 ,3,
                                     5 ,4 ,7,   5 ,7 ,6};
        //绘制时的顺序(索引)  索引顺序会造成三角形朝向的改变(顺时针,逆时针)
        mesh.RecalculateNormals();//计算法线信息 (计算光照) 不然会不亮
        GetComponent<MeshFilter>().mesh = mesh;//获取组件并赋值网格

        Material mat = new Material(Shader.Find("Standard")); //创建材质球  Shader.Find("着色器的名字")
        GetComponent<MeshRenderer>().material = mat;//赋值材质球
	这里是圆柱体
	 List<Vector3> vertices = new List<Vector3>();//创建点的容器
	 List<int> triangleIndex = new List<int>();//三角形索引
     vertices.Clear();
        vertices.Add(new Vector3(0, 0, 0));//添加圆心
        int n = 50;//顶点的个数
        float rad = 2 * Mathf.PI / n;//计算弧度
        //  float rad=360*n*Mathf.Deg2Rad; 计算弧度 两种方法用哪种都可以
        for (int i = 0; i < n; i++)
        {
            float x = Mathf.Cos(rad * i);
            float z = Mathf.Sin(rad * i);
            vertices.Add(new Vector3(x, 0, z));//添加计算完后的点
            if (i == 0)
            {//判断i为0的情况画三角形
                triangleIndex.Add(0);
                triangleIndex.Add(1);
                triangleIndex.Add(n);
            }
            else
            {//根据规律判断其他情况
                triangleIndex.Add(0);
                triangleIndex.Add(i + 1);
                triangleIndex.Add(i);
            }
        }
        vertices.Add(new Vector3(0, -5, 0));//添加下圆心
        for (int i = 0; i < n; i++)
        {
            float x = Mathf.Cos(rad * i);
            float z = Mathf.Sin(rad * i);
            vertices.Add(new Vector3(x, -5, z));//添加计算完后的点
            if (i == 0)
            {
                triangleIndex.Add(n + 1);
                triangleIndex.Add(n + 1 + n);
                triangleIndex.Add(n + 1 + 1);
            }
            else
            {
                triangleIndex.Add(n + 1);
                triangleIndex.Add(n + 1 + i);
                triangleIndex.Add(n + 1 + i + 1);
            }
        }
        for (int i = 0; i < n; i++)
        {

            if (i == 0)
            {
                triangleIndex.Add(1);
                triangleIndex.Add(n + 1 + 1);
                triangleIndex.Add(n + 1 + n);

                triangleIndex.Add(n);
                triangleIndex.Add(1);
                triangleIndex.Add(n + 1 + n);
            }
            else
            {
                triangleIndex.Add(i + 1);
                triangleIndex.Add(n + 1 + i + 1);
                triangleIndex.Add(n + 1 + i);

                triangleIndex.Add(i);
                triangleIndex.Add(i + 1);
                triangleIndex.Add(n + 1 + i);

            }
        }
        mesh = new Mesh();
        mesh.vertices = vertices.ToArray();//转换成数组
        mesh.triangles = triangleIndex.ToArray();//圆形索引数组

        mesh.RecalculateNormals();//计算法线信息 (计算光照) 不然会不亮
        GetComponent<MeshFilter>().mesh = mesh;//获取组件并赋值网格

        Material mat = new Material(Shader.Find("Standard")); //创建材质球  Shader.Find("着色器的名字")
        GetComponent<MeshRenderer>().material = mat;//赋值材质球

	这里是管道
		 public void NewPipeline()
	    {
        vertices.Clear();
        triangleIndex.Clear();
        int n = 50;
        // int n2 = 20;
        float rad = 2 * Mathf.PI / n;//计算弧度
                                     // float rad2 = 2 * Mathf.PI / n2;//计算弧度
        vertices.Add(new Vector3(0, 0, 0));
        for (int i = 0; i < n; i++)
        {
            float y = Mathf.Sin(rad * i);
            float x = Mathf.Cos(rad * i);

            vertices.Add(new Vector3(x, 0, y));//添加上层内圈点
        }
        for (int i = 0; i < n; i++)
        {
            float y = Mathf.Sin(rad * i) * 2;
            float x = Mathf.Cos(rad * i) * 2;

            vertices.Add(new Vector3(x, 0, y));//添加上层外圈点
            if (i == 0)
            {
                triangleIndex.Add(1);
                triangleIndex.Add(2 * n);
                triangleIndex.Add(n);

                triangleIndex.Add(1);
                triangleIndex.Add(n + 1);
                triangleIndex.Add(2 * n);

            }
            else
            {
                triangleIndex.Add(i);
                triangleIndex.Add(i + 1);
                triangleIndex.Add(n + i + 1);

                triangleIndex.Add(i);
                triangleIndex.Add(n + i + 1);
                triangleIndex.Add(n + i);
            }

        }
        for (int i = 0; i < n; i++)
        {
            float y = Mathf.Sin(rad * i);
            float x = Mathf.Cos(rad * i);
            vertices.Add(new Vector3(x, -5, y));//添加下层内圈点
        }
        for (int i = 0; i < n; i++)
        {
            float y = Mathf.Sin(rad * i) * 2;
            float x = Mathf.Cos(rad * i) * 2;
            vertices.Add(new Vector3(x, -5, y));//添加下层外圈点
            if (i == 0)
            {
                triangleIndex.Add(2 * n + 1);
                triangleIndex.Add(3 * n);
                triangleIndex.Add(4 * n);

                triangleIndex.Add(2 * n + 1);
                triangleIndex.Add(4 * n);
                triangleIndex.Add(3 * n + 1);
            }
            else
            {
                triangleIndex.Add(i + 2 * n);
                triangleIndex.Add(n + i + 1 + 2 * n);
                triangleIndex.Add(i + 1 + 2 * n);


                triangleIndex.Add(i + 2 * n);
                triangleIndex.Add(n + i + 2 * n);
                triangleIndex.Add(n + i + 1 + 2 * n);
            }
        }
        for (int i = 0; i < n; i++)
        {
            if (i == 0)
            {
                triangleIndex.Add(n);
                triangleIndex.Add(3 * n);
                triangleIndex.Add(2 * n + 1);

                triangleIndex.Add(1);
                triangleIndex.Add(n);
                triangleIndex.Add(2 * n + 1);
            }
            else
            {
                triangleIndex.Add(i);
                triangleIndex.Add(2 * n + i);
                triangleIndex.Add(2 * n + i + 1);

                triangleIndex.Add(i);
                triangleIndex.Add(2 * n + i + 1);
                triangleIndex.Add(i + 1);
            }
        }
        for (int i = 0; i < n; i++)
        {
            if (i == 0)
            {
                triangleIndex.Add(n + n);
                triangleIndex.Add(2 * n + 1 + n);
                triangleIndex.Add(3 * n + n);

                triangleIndex.Add(1 + n);
                triangleIndex.Add(2 * n + 1 + n);
                triangleIndex.Add(n + n);
            }
            else
            {
                triangleIndex.Add(i + n);
                triangleIndex.Add(2 * n + i + 1 + n);
                triangleIndex.Add(2 * n + i + n);

                triangleIndex.Add(i + n);
                triangleIndex.Add(i + 1 + n);
                triangleIndex.Add(2 * n + i + 1 + n);
            }
        }
        mesh = new Mesh();
        mesh.vertices = vertices.ToArray();//转换成数组
        mesh.triangles = triangleIndex.ToArray();//圆形索引数组

        // mesh.RecalculateNormals();//计算法线信息 (计算光照) 不然会不亮
        GetComponent<MeshFilter>().mesh = mesh;//获取组件并赋值网格

        Material mat = new Material(Shader.Find("Standard")); //创建材质球  Shader.Find("着色器的名字")
        GetComponent<MeshRenderer>().material = mat;//赋值材质球
	物理碰撞
	  transform.AddComponent<MeshCollider>().convex=true; //注意要把这里的选项调成true
		碰撞检测需要双方有碰撞器,而一方有刚体
	正方形贴图
		 mesh = new Mesh();
        Vector3[] vertices = new Vector3[24];

        vertices[0] = new Vector3(1, 0, 0);//前
        vertices[1] = new Vector3(0, 0, 0);
        vertices[2] = new Vector3(1, 1, 0);
        vertices[3] = new Vector3(0, 1, 0);

        vertices[4] = new Vector3(1, 0, 1);//后
        vertices[5] = new Vector3(0, 0, 1);
        vertices[6] = new Vector3(1, 1, 1);
        vertices[7] = new Vector3(0, 1, 1);

        vertices[8] = vertices[1];//左
        vertices[9] = vertices[5];
        vertices[10] = vertices[3];
        vertices[11] = vertices[7];

        vertices[12] = vertices[4];//右
        vertices[13] = vertices[0];
        vertices[14] = vertices[6];
        vertices[15] = vertices[2];

        vertices[16] = vertices[2];//上
        vertices[17] = vertices[3];
        vertices[18] = vertices[6];
        vertices[19] = vertices[7];

        vertices[20] = vertices[4];//下
        vertices[21] = vertices[5];
        vertices[22] = vertices[0];
        vertices[23] = vertices[1];

        mesh.vertices = vertices;
        mesh.triangles = new int[] { 3, 2, 0, 3, 0, 1,
            6, 7, 5, 4, 6, 5,
            10,9, 11, 10, 8, 9,
            14, 13, 15, 14, 12, 13,
            19, 18, 17, 18, 16, 17,
            20, 21, 23, 20, 23, 22 };
        mesh.uv = new Vector2[] { new Vector2(1/2f,1/3f), new Vector2(1 / 4f, 1 / 3f), new Vector2(1 / 2f,0), new Vector2(1 / 4f, 0),
             new Vector2(1/2f,2/3f), new Vector2(1 / 4f, 2 / 3f), new Vector2(1 / 2f,1), new Vector2(1 / 4f, 1),
              new Vector2(1/4f,2/3f), new Vector2(1 / 4f, 1 / 3f), new Vector2(0,1/3f), new Vector2(0, 2/3f),
               new Vector2(1/2f,2/3f), new Vector2(1 / 2f, 1 / 3f), new Vector2(3 / 4f,2/3f), new Vector2(3 / 4f, 1/3f),
                new Vector2(3/4f,1/3f), new Vector2(1, 1 / 3f), new Vector2(3 / 4f,2/3f), new Vector2(1, 2/3f),
                 new Vector2(1/2f,2/3f), new Vector2(1 / 4f, 2 / 3f), new Vector2(1 / 2f,1/3f), new Vector2(1 / 4f, 1/3f)
        };

        mesh.RecalculateNormals();//计算法线信息 (计算光照) 不然会不亮
        mesh.RecalculateBounds();
        GetComponent<MeshFilter>().mesh = mesh;//获取组件并赋值网格

        Material mat = new Material(Shader.Find("Standard")); //创建材质球  Shader.Find("着色器的名字")
        mat.mainTexture = texture;
	        GetComponent<MeshRenderer>().material = mat;//赋值材质球
	圆形贴图
		int n = 50;
        float rad = 2 * Mathf.PI / n;
        float r = 5;
        mesh = new Mesh();
        vertices.Clear();
        triangleIndex.Clear();
        vertices.Add(new Vector3(0, 0, 0));
        uvs.Add(new Vector2(0.5f,0.5f));
        for (int i = 0; i < n; i++)
        {
            float x = Mathf.Cos(rad * i) * r;
            float y = Mathf.Sin(rad * i) * r;
            vertices.Add(new Vector3(x, 0, y));
            float u = (x + r) / (2 * r);
            float v = (y + r) / (2 * r);
            uvs.Add(new Vector2(u, v));

        }
        for (int i = 0; i < n; i++)
        {
            if (i == 0)
            {
                triangleIndex.Add(0);
                triangleIndex.Add(1);
                triangleIndex.Add(n);
            }
            else
            {
                triangleIndex.Add(0);
                triangleIndex.Add(i + 1);
                triangleIndex.Add(i);
            }
        }
        mesh.vertices = vertices.ToArray();
        mesh.triangles = triangleIndex.ToArray();
        mesh.uv = uvs.ToArray();
        mesh.RecalculateNormals();
      
        GetComponent<MeshFilter>().mesh = mesh;
        Material mat = new Material(Shader.Find("Standard"));
        mat.mainTexture=texture;
        GetComponent<MeshRenderer>().material = mat;
	圆形贴图取中间
	 for (int i = 0; i < n; i++)
        {
            float x = Mathf.Cos(rad * i) * r;
            float y = Mathf.Sin(rad * i) * r;
            vertices.Add(new Vector3(x, 0, y));
            float x2= Mathf.Cos(rad * i) * 3;//这里乘以一个比半径小的数字,就能实现取终点图形
            float y2= Mathf.Sin(rad * i) * 3;
            float u = (x2 + r) / (2 * r);//u和v 也使用小半径uv 坐标来显示
            float v = (y2 + r) / (2 * r);
            uvs.Add(new Vector2(u, v));

        }
    蜘蛛网
     using System.Collections;
	 using System.Collections.Generic;
	 using UnityEngine;
	 using UnityEngine.UI;

	 namespace NinjaGame
	 {
     [RequireComponent(typeof(CanvasRenderer))]
     public class SpiderWeb : MaskableGraphic
	    {
        [field: SerializeField]
        public float Size { get; set; } = 100;//直径

        [field: SerializeField]
        public int VertexCount { get; set; } = 6;//顶点数量

        [field: SerializeField]
        public int LineCount { get; set; } = 5;//边的数量

        [field: SerializeField]
        public float LineThickness { get; set; } = 1;//线的厚度

        protected override void OnPopulateMesh(VertexHelper vh)
        {
            var radius = Size / 2;                            // 半径
            var vertexCount = VertexCount;                    // 顶点数量
            var lineCount = LineCount;                        // 线条数量
            var lineThickness = LineThickness;                // 线条厚度
            var halfLineThickness = lineThickness / 2;        // 线条厚度的一半
            var radianGap = Mathf.PI * 2 / vertexCount;       // 弧度间隔

            vh.Clear();

            // 循环每一条线
            for (int i = 0; i < lineCount; i++)
            {
                var outerRadius = radius - (radius * i / lineCount);                     // 这条线外部半径
                var innerRadius = radius - (radius * i / lineCount) - lineThickness;     // 这条线内部半径
                var lineVertexIndexOffset = vh.currentVertCount;                         // 当前边顶点索引偏移量  

                // 循环每一个顶点
                for (int j = 0; j < vertexCount; j++)
                {
                    var radian = radianGap * j;            // 当前顶点角度
                    var cos = Mathf.Cos(radian);           // COS 值
                    var sin = Mathf.Sin(radian);           // SIN 值

                    var outerX = cos * outerRadius;        // 外部顶点的 X 坐标
                    var outerY = sin * outerRadius;        // 外部顶点的 Y 坐标

                    var innerX = cos * innerRadius;        // 内部顶点的 X 坐标
                    var innerY = sin * innerRadius;        // 内部顶点的 Y 坐标

                    var currentOuterVertexIndex = lineVertexIndexOffset + j * 2;                          // 当前角外部顶点的索引
                    var currentInnerVertexIndex = lineVertexIndexOffset + j * 2 + 1;                      // 当前角内部顶点的索引
                    var nextOuterVertexIndex = lineVertexIndexOffset + (j + 1) % vertexCount * 2;         // 下一个角外部顶点的索引
                    var nextInnerVertexIndex = lineVertexIndexOffset + (j + 1) % vertexCount * 2 + 1;     // 下一个角内部顶点的索引

                    // 添加两个顶点
                    vh.AddVert(new Vector3(outerX, outerY), color, new Vector4());
                    vh.AddVert(new Vector3(innerX, innerY), color, new Vector4());

                    // 添加两个三角形
                    vh.AddTriangle(currentInnerVertexIndex, nextInnerVertexIndex, nextOuterVertexIndex);
                    vh.AddTriangle(currentInnerVertexIndex, nextOuterVertexIndex, currentOuterVertexIndex);
                }
            }


            for (int i = 0; i < vertexCount; i++)
            {
                var outerRadius = radius - lineThickness / 2;           // 外部半径
                var vertexIndexOffset = vh.currentVertCount;

                var radian = radianGap * i;                             // 当前方向角度
                var cos = Mathf.Cos(radian);                            // 当前角度 COS 值
                var sin = Mathf.Sin(radian);                            // 当前角度 SIN 值
                var tanCos = Mathf.Cos(radian - Mathf.PI / 2);          // 当前方向切线的 COS 值
                var tanSin = Mathf.Sin(radian - Mathf.PI / 2);          // 当前方向切线的 SIN 值
                var sideX = cos * outerRadius;
                var sideY = sin * outerRadius;

                var centerPoint0 = new Vector3(tanCos * halfLineThickness, tanSin * halfLineThickness);
                var centerPoint1 = -centerPoint0;

                var sidePoint0 = new Vector3(sideX + centerPoint0.x, sideY + centerPoint0.y);
                var sidePoint1 = new Vector3(sideX + centerPoint1.x, sideY + centerPoint1.y);

                vh.AddVert(centerPoint0, color, new Vector4());
                vh.AddVert(centerPoint1, color, new Vector4());
                vh.AddVert(sidePoint0, color, new Vector4());
                vh.AddVert(sidePoint1, color, new Vector4());

                vh.AddTriangle(vertexIndexOffset, vertexIndexOffset + 1, vertexIndexOffset + 3);
                vh.AddTriangle(vertexIndexOffset, vertexIndexOffset + 3, vertexIndexOffset + 2);
            }
        }
		  }
		 }
	灰度图
		public Texture2D _texture2D;
	    public float HeightScale = 1;
	
	    Mesh mesh;
	    VertexHelper vh;
	    //int w = 200;
	    //int h = 200;
	    void Start()
	    {
	        mesh = new Mesh();
	        vh = new VertexHelper();
	        vh.Clear();
	
	        for (int x = 0; x < _texture2D.width; x++)
	        {
	            for (int z = 0; z < _texture2D.height; z++)
	            {
	                float y = _texture2D.GetPixel(x, z).grayscale;//取出灰度值
	                vh.AddVert(new Vector3(x, y * HeightScale, z), Color.red, new Vector2());
	                // 添加三角形
	                if (x > 0 && z > 0)
	                {
	                    int currentIndex = x * _texture2D.height + z;
	                    int bottomLeft = (x - 1) * _texture2D.height + z;
	                    int bottomRight = (x - 1) * _texture2D.height + (z - 1);
	                    int topLeft = x * _texture2D.height + (z - 1);
	
	                    vh.AddTriangle( currentIndex, bottomRight, bottomLeft);
	                    vh.AddTriangle(currentIndex, topLeft, bottomRight);
	                }
	            }
	        }
	        vh.FillMesh(mesh);
	        mesh.RecalculateNormals();
	
	        transform.GetOrAddComponent<MeshFilter>().mesh = mesh;
	        transform.GetOrAddComponent<MeshRenderer>().material = new Material(Shader.Find("Standard"));
	合并网格和材质
		 public GameObject[] AllGameobject;//接收所有的游戏对象
	    void Start()
	    {
	        CombineGameObjecct(AllGameobject);
	    }
	    public void CombineGameObjecct(GameObject[] gameObjects)
	    {
	        Material material = null;//定义材质
	        List<Vector2[]> allV2 = new List<Vector2[]>();//存放每个对象的uv数组
	        List<Texture2D> texture2Ds = new List<Texture2D>();//存放每个游戏对象的主纹理
	        List<CombineInstance> combineInstances = new List<CombineInstance>();//存放组合对象
	        for (int i = 0; i < gameObjects.Length; i++)
	        {
	            //获取组件
	            var mashRenderer = gameObjects[i].GetComponent<MeshRenderer>();
	            var meshFilter = gameObjects[i].GetComponent<MeshFilter>();
	
	            //判空,空就赋值一个材质
	            if (material == null)
	                material = Instantiate(mashRenderer.material);
	
	            //把数据都添加进容器
	            allV2.Add(meshFilter.mesh.uv);
	            texture2Ds.Add(mashRenderer.material.mainTexture as Texture2D);
	            combineInstances.Add(new CombineInstance()
	            {
	                mesh = meshFilter.mesh,
	                transform = gameObjects[i].transform.localToWorldMatrix
	            });
	
	
	        }
	        //创建网格
	        Mesh mesh = new Mesh();
	        mesh.CombineMeshes(combineInstances.ToArray());//组合网格
	
	        //组合材质
	        Texture2D texture2D = new Texture2D(0, 0);
	        Rect[] r = texture2D.PackTextures(texture2Ds.ToArray(), 0);//返回每个材质在当前纹理中的位置矩阵
	
	        material.mainTexture = texture2D;//赋值纹理
	        Vector2[] Newv2 = new Vector2[mesh.uv.Length];//创建新uv容器
	
	        //遍历所有游戏对象的uv 数组
	        for (int i = 0, j = 0; i < allV2.Count; i++)
	        {
	            Rect rect = r[i];//找当当前游戏对象在当前矩阵中的矩阵位置
	
	            //遍历uv数组
	            foreach (var item in allV2[i])
	            {
	                //计算当前的uv坐标
	                Newv2[j].x = Mathf.Lerp(rect.xMin, rect.xMax, item.x);
	                Newv2[j].y = Mathf.Lerp(rect.yMin, rect.yMax, item.y);
	                j++;
	            }
	        }
	        //赋值
	        mesh.uv = Newv2;
	        GetComponent<MeshFilter>().mesh = mesh;
	        GetComponent<MeshRenderer>().material = material;
	2D轮转图
		  // Start is called before the first frame update
		    //存放所有materia
		    public GameObject Avater;
		    [SerializeField]
		    GameObject _image;
		
		    [SerializeField]
		    List<Sprite> materials = new List<Sprite>();
		
		
		    public List<Sprite> materialsList
		    {
		        get => materials;
		        set
		        {
		            materials = value;
		        }
		
		    }
		
		    public GameObject MaterialImage
		    {
		        get => _image;
		        set
		        {
		            _image = value;
		        }
		
		    }
		
		
		
		    [field: SerializeField]
		    public int Space { get; set; } = 100;
		    [field: SerializeField]
		    public int Speed { get; set; } = 100;
		    [field: SerializeField]
		    public float Max { get; set; } = 1;
		    [field: SerializeField]
		    public float Min { get; set; } = 0.4f;
		
		    float _radius;
		    float _radian;
		    float _moveRadian;//移动时的弧度
		    List<GameObject> cells = new List<GameObject>();
		    List<GameObject> sorts = new List<GameObject>();
		
		    void Start()
		    {
		        _radian = Mathf.PI * 2 / materialsList.Count;//计算弧度
		        _radius = materialsList.Count * (MaterialImage.GetComponent<RectTransform>().sizeDelta.x + Space) / (2 * Mathf.PI);//计算半径
		        Move();
		    }
		    /// <summary>
		    /// 移动方法
		    /// </summary>
		    private void Move()
		    {
		        for (int i = 0; i < materialsList.Count; i++)
		        {
		            float x = Mathf.Cos(_radian * i + _moveRadian) * _radius;
		            float z = Mathf.Sin(_radian * i + _moveRadian) * _radius;
		            if (cells.Count <= i)
		            {
		                GameObject NewImage = Instantiate(MaterialImage, Vector3.zero, Quaternion.identity, transform);
		                NewImage.GetComponent<Image>().sprite = materialsList[i];//赋值材质
		                NewImage.transform.name = i.ToString();
		                NewImage.SetActive(true);
		                cells.Add(NewImage);
		                sorts.Add(NewImage);
		            }
		            float _scale = (z + _radius) / (2 * _radius) * (Max - Min) + Min;
		            cells[i].transform.localScale = new Vector3(_scale, _scale, _scale);
		            cells[i].transform.localPosition = new Vector3(x, 0, 0);
		        }
		        sorts = sorts.OrderBy(x => x.transform.lossyScale.z).ToList();
		        for (int i = 0; i < sorts.Count; i++)
		        {
		            sorts[i].transform.SetSiblingIndex(i);
		        }
		    }
		
		    public void OnEndDrag(PointerEventData eventData)
		    {
		        float tempRadian = Mathf.Asin(sorts[sorts.Count - 1].transform.localPosition.x / _radius);
		        float distance = tempRadian * _radius;
		        float time = distance / Speed;
		        DOTween.To((x) =>
		        {
		            _moveRadian = x;
		            Move();
		        }, _moveRadian, _moveRadian + tempRadian, time).OnComplete(() =>
		        {
		
		            if (transform.name == "Tou")
		            {
		                GameObject maxImage = sorts.OrderBy(x => x.transform.lossyScale.z).Last();
		
		                Avater.GetComponent<TestHz>().ChangeCloths(1, int.Parse(maxImage.name));
		            }
		            else
		            {
		                GameObject maxImage = sorts.OrderBy(x => x.transform.lossyScale.z).Last();
		
		                Avater.GetComponent<TestHz>().ChangeCloths(3, int.Parse(maxImage.name));
		            }
		
		
		        });
		    }
		
		    public void OnDrag(PointerEventData eventData)
		    {
		        _moveRadian -= eventData.delta.x / _radius;
		        Move();
		    }
		}
		
		    }
				
				
		    }
```

#VertexHelper
VertexHelper 是 Unity 中用于修改和操作 UI 顶点数据的辅助类。通过 VertexHelper，你可以创建、修改和渲染 UI 元素的顶点信息。

VertexHelper 提供了一系列方法来添加、修改和操作顶点数据。以下是一些常用的 VertexHelper 方法：

1. `AddVert(Vector3 position, Color32 color, Vector2 uv0)`：添加一个顶点到 VertexHelper 中，指定位置、颜色和 UV 坐标。
    
2. `AddTriangle(int vertexIndex1, int vertexIndex2, int vertexIndex3)`：添加一个三角形，指定三个顶点的索引。
    
3. `SetUIVertex(UIVertex vertex, int index)`：设置指定索引处的顶点信息。
    
4. `FillMesh(Mesh mesh)`：将 VertexHelper 中的顶点数据填充到指定的 Mesh 对象中。
    

这些方法可以让你直接操作顶点数据，例如添加、修改和删除顶点，以及设置顶点的位置、颜色和 UV 坐标。一般情况下，你需要使用这些方法来构建自定义 UI 元素或对现有的 UI 元素进行更高级的操作。