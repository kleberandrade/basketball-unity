# Basketball

A free throw in basketball in Unity 3D

<p align="center">
  <img width="600" src="Images/">
</p>

## Methods

## Codes

### Throw Ball

```csharp
public class ThrowBall : MonoBehaviour
{
    public Rigidbody m_BallPrefab;
    public float m_Force = 10.0f;

    private Camera m_Camera;

    public void Awake()
    {
        m_Camera = GetComponentInChildren<Camera>();
    }

    public void Update()
    {
        if (Input.GetButtonDown("Fire1")){
            Rigidbody ball = Instantiate<Rigidbody>(m_BallPrefab);
            ball.transform.position = transform.position;
            ball.velocity = m_Camera.transform.rotation * Vector3.forward * m_Force;
        }
    }
}
```

### Mouse LookAt

```csharp
public class CameraRotationWithMouse : MonoBehaviour
{
    public float m_RotationSpeed = 5.0f;

    private Camera m_Camera;

    public void Awake()
    {
        m_Camera = GetComponentInChildren<Camera>();
    }

    public void Update()
    {
        float mouseX = Input.GetAxis("Mouse X") * m_RotationSpeed;
        float mouseY = Input.GetAxis("Mouse Y") * m_RotationSpeed;

        transform.localRotation = Quaternion.Euler(0, mouseX, 0) * transform.localRotation;
        m_Camera.transform.localRotation = Quaternion.Euler(-mouseY, 0, 0) * m_Camera.transform.localRotation;
    }
}
```

## Acknowledgement

To my friend Dalvan Cezar for modeling the scenary

## License

    Copyright 2019 Kleber de Oliveira Andrade
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
