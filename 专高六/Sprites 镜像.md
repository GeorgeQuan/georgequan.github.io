```c#
using UnityEngine;
using UnityEngine.UI;

public class HalfImageMirrorAndCombine : MonoBehaviour
{
    public Image imageToMirror; // 需要镜像的图像组件

    void Start()
    {
        MirrorAndCombineHalfImage(imageToMirror);
    }

    void MirrorAndCombineHalfImage(Image image)
    {
        if (image.sprite == null) return;

        Texture2D originalTexture = image.sprite.texture;
        Texture2D mirroredTexture = new Texture2D(originalTexture.width, originalTexture.height);

        // 复制原始纹理的像素
        Color[] pixels = originalTexture.GetPixels();
        mirroredTexture.SetPixels(pixels);

        // 反转一半的像素
        for (int y = 0; y < originalTexture.height; y++)
        {
            for (int x = 0; x < originalTexture.width / 2; x++)
            {
                Color temp = mirroredTexture.GetPixel(x, y);
                mirroredTexture.SetPixel(x, y, mirroredTexture.GetPixel(originalTexture.width - x - 1, y));
                mirroredTexture.SetPixel(originalTexture.width - x - 1, y, temp);
            }
        }

        // 应用修改
        mirroredTexture.Apply();

        // 创建一个新的纹理，用于合并两个纹理
        Texture2D combinedTexture = new Texture2D(originalTexture.width * 2, originalTexture.height);

        // 将原始纹理的像素复制到新纹理的左半部分
        for (int y = 0; y < originalTexture.height; y++)
        {
            for (int x = 0; x < originalTexture.width; x++)
            {
                combinedTexture.SetPixel(x, y, originalTexture.GetPixel(x, y));
            }
        }

        // 将镜像纹理的像素复制到新纹理的右半部分
        for (int y = 0; y < originalTexture.height; y++)
        {
            for (int x = 0; x < originalTexture.width; x++)
            {
                combinedTexture.SetPixel(x + originalTexture.width, y, mirroredTexture.GetPixel(x, y));
            }
        }

        // 应用修改
        combinedTexture.Apply();

        // 更新图像
        Sprite newSprite = Sprite.Create(combinedTexture, new Rect(0, 0, combinedTexture.width, combinedTexture.height), new Vector2(0.5f, 0.5f));
        image.sprite = newSprite;
    }
}
```