public class Player : MonoBehaviour
{
    public float speed;
    public FixedJoystick joyStick;

    Rigidbody2D rigid;
    SpriteRenderer spriter;
    Animator anima;

    void Awake()
    {
        rigid = GetComponent<Rigidbody2D>();
        spriter = GetComponent<SpriteRenderer>();
        anima = GetComponent<Animator>();
        rigid.drag = 10f; // 적절한 값을 설정합니다.
        rigid.angularDrag = 10f; // 적절한 값을 설정합니다.
    }

    void Update()
    {
        Vector2 inputVec = new Vector2(Input.GetAxisRaw("Horizontal"), Input.GetAxisRaw("Vertical"));
        if (joyStick != null)
        {
            Vector2 joystickInput = new Vector2(joyStick.Horizontal, joyStick.Vertical);
            if (joystickInput.magnitude > 0.1f)
            {
                inputVec = joystickInput;
            }
        }

        anima.SetFloat("Speed", inputVec.magnitude);
        if (inputVec.x != 0)
        {
            spriter.flipX = inputVec.x < 0;
        }

        Vector2 nextVec = inputVec.normalized * speed;
        rigid.velocity = nextVec;
    }
}
